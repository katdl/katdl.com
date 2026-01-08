---
title: "Assessing Agreement Among Doctors on Diagnosis"
date: 2021-10-31
slug: "agreement"
categories:
  - medical
  - stats
tags:
  - medical
  - stats
authors:
  - matt
summary: "Using Fleiss' kappa in R to measure agreement between multiple doctors when classifying patient diagnoses."
---

When a doctor builds a new model for understanding different diagnosis and evaluations
it can be tricky to figure out how clearly it works.

One way to do that is to look at a significant number of patients and compare how strongly
a group of doctors agreed in their evaluations.

In this post, we talk about how we did that using Fleiss kappa in R.

## Fleiss Kappa

Fleiss' kappa helps us to understand the level of agreement between raters when classifying
items. (Additional detail around the statistics is on [Wikipedia](https://en.wikipedia.org/wiki/Fleiss'_kappa))

We chose the Fleiss kappa because it supports multiple raters while some other kappas
(eg. Cohen's kappa) only support two raters.

Fleiss' kappa does depend on being able to look at data that has been categorized and
luckily that fit our use case and we had the data to support it.

## Choosing Our Tools

Although python is usually our first tool of choice for analyzing data, in this case we did not
readily identify built in stats libraries that handle the Fleiss kappa. While the algorithm
could be written from scratch based on the formula, or copied from a stack overflow
article - instead of doing either of those things, we elected to expand our toolset to
R which has a library that supports various kappa, including the Fleiss kappa.

Getting set up was easy using conda and Jupyter notebooks:

```sh
conda create -n dataplay r-essentials r-base
conda activate dataplay
conda install Jupyter
conda install r-irr
R -e 'IRkernel::installspec()'
jupyter-notebook
```

## Normalizing Data

What the Fleiss kappa expects, is a matrix of N subjects by M raters.

Our incoming data didn't look like that, it had a row per subject (patient)
per rater (doctor). So we just wrote a python script to transform the data
to this structure.

Well and actually the data had three different types of assessments for
each patient and doctor. So we build three separate files for each of the
scenarios and just calculated the kappa independently.

## Applying the Kappa

Turns out once you have the data in the right format, applying the kappa
is as simple as:

```R
data <-read.csv("specific.csv", header=FALSE)
kappam.fleiss(data, exact=FALSE, detail=TRUE)
```

The result was cool because with the detail, it not only shows how much
the doctors agree, but also how much they agree on each diagnosis.

```txt
 Subjects = 173
   Raters = 4
    Kappa = 0.788

        z = 51.4
  p-value = 0

         Kappa      z p.value
1        0.948 30.553   0.000
2        0.803 25.857   0.000
3        0.646 20.826   0.000
4        0.747 24.051   0.000
5        0.883 28.463   0.000
6        0.893 28.756   0.000
Unknown -0.009 -0.282   0.778
```

The results are a summary count of raters and subjects:
- Kappa:    Are they agreeing (1) or disagreeing (-1)?
- z:        a "standard score"
- p-value:  < 0.05 is an indication agreement is not just chance. Not predictive.

## Conclusion

It is amazing to work with doctors who already have interesting data and just need
a little help building the programming or statistics or data analysis around it.
This exercise took just a few hours but provided very quick and useful input back
to the team that requested it.

Using R turned out to be easy and seamless. I expect we will deliver more solutions
in Jupyter notebooks in the future as well.

## References

- [Fleiss kappa](https://en.wikipedia.org/wiki/Fleiss'_kappa)
- [R Fleiss kappa documentation](https://www.rdocumentation.org/packages/irr/versions/0.84.1/topics/kappam.fleiss)
- [Cohen's kappa](https://en.wikipedia.org/wiki/Cohen%27s_kappa)
