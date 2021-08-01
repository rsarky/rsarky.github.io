---
layout: post
title: Bayes in the wild
date: 2021-08-02 00:16 +0530
---
Today one of my friends forwarded me this message on Whatsapp:


> Israel now provides vaccination status among new coronavirus cases and those
  who are seriously ill.
>
> New cases (Sat): -
>
> Unvaccinated: 1,006  Partially vaccinated: 39  Fully vaccinated: 1,049
>
> Seriously ill: 
>
> Unvaccinated: 71 
  Partially vaccinated: 7 
  Fully vaccinated: 133)

Note that I am not sure if the data is reliable here. Let us assume that the
given data is accurate. On first glance this can be interpreted to mean that
vaccines are inefficient, since the number of vaccinated people among the
number of new cases is more than the number of unvaccinated people. And
similarly for the number of seriously ill cases. This is dangerous since
vaccine skeptics base their arguments on statistics like these.

However, this interpretation is flawed since we disregard one important
statistic: the proportion of vaccinated individuals in the population (aka the
_base rate_). If a large proportion of the population has been vaccinated it
would imply that the proportion of vaccinated individuals among new cases will
also be large.  Ignoring the actual proportion of vaccinated individuals is a
typical example of the [base rate
fallacy](https://en.wikipedia.org/wiki/Base_rate_fallacy).  This is actually
just Bayes theorem in disguise.

To drive this point home we can play around with some numbers. Consider for
instance that 85% of Israel's population is vaccinated and vaccines are 70%
effective. Further the probability of a test being positive given that someone
is not vaccinated is say 50%. To simplify things we only consider single dose
vaccinations.
Now we want to find P(vaccinated | cov+) or the probability that someone is
vaccinated given that the person has been tested covid positive.
Applying Bayes theorem this can be reframed as:

$$P(Vaxed|+)=\frac{P(+|Vaxed)P(Vaxed)}{P(+|Vaxed)P(Vaxed)+P(+|Unvaxed)P(Unvaxed)}$$

$$=\frac{0.3 \times 0.85}{0.3 \times 0.85 + 0.5 \times 0.15}$$

$$=0.77$$

Thus this shows that given these imaginary but plausible numbers one could
expect 77% of covid positive people to have been vaccinated.
As more and more people are getting vaccinated we can expect an uptick in the
number of vaccinated peoples getting infected, not because vaccines are
inefficient but just because so many people are getting vaccinated.
