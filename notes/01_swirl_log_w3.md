# WEEK 3


Selection: 9

| Attempting to load lesson dependencies...

| Package ‘ggplot2’ loaded correctly!

| Package ‘jpeg’ loaded correctly!

  |                                                                              |   0%

| T_Confidence_Intervals. (Slides for this and other Data Science courses may be found
| at github https://github.com/DataScienceSpecialization/courses/. If you care to use
| them, they must be downloaded as a zip file and viewed locally. This lesson
| corresponds to 06_Statistical_Inference/08_tCIs.)

...

  |=                                                                             |   1%
| In this lesson, we'll discuss some statistical methods for dealing with small
| datasets, specifically the Student's or Gosset's t distribution and t confidence
| intervals.

...

  |==                                                                            |   3%
| In the Asymptotics lesson we discussed confidence intervals using the Central Limit
| Theorem (CLT) and normal distributions. These needed large sample sizes, and the
| formula for computing the confidence interval was Est +/- qnorm *std error(Est),
| where Est was some estimated value (such as a sample mean) with a standard error.
| Here qnorm represented what?

1: the population variance
2: the standard error
3: the population mean
4: a specified quantile from a normal distribution

Selection: 4

| You're the best!

  |===                                                                           |   4%
| In the Asymptotics lesson we also mentioned the Z statistic
| Z=(X'-mu)/(sigma/sqrt(n)) which follows a standard normal distribution. This
| normalized statistic Z is especially nice because we know its mean and variance.
| They are what, respectively?

1: 0 and 1
2: 1 and 1
3: 1 and 0
4: 0 and 0

Selection: 1

| Excellent job!

  |====                                                                          |   5%
| So the mean and variance of the standardized normal are fixed and known. Now we'll
| define the t statistic which looks a lot like the Z. It's defined as
| t=(X'-mu)/(s/sqrt(n)). Like the Z statistic, the t is centered around 0. The only
| difference between the two is that the population std deviation, sigma, in Z is
| replaced by the sample standard deviation in the t. So the distribution of the t
| statistic is independent of the population mean and variance. Instead it depends on
| the sample size n.

...

  |=====                                                                         |   7%
| As a result, for t distributions, the formula for computing a confidence interval is
| similar to what we did in the last lesson. However, instead of a quantile for a
| normal distribution we use a quantile for a t distribution. So the formula is Est
| +/- t-quantile *std error(Est). The other distinction, which we mentioned before, is
| that we'll use the sample standard deviation when we estimate the standard error of
| Est.

...

  |======                                                                        |   8%
| In the formula for the t statistic t=(X'-mu)/(s/sqrt(n)) what expression represents
| the sample standard deviation?

1: s
2: n
3: mu
4: X'

Selection: 1

| Perseverance, that's the answer.

  |=======                                                                       |   9%
| These t confidence intervals are very handy, and if you have a choice between these
| and normal, pick these. We'll see that as datasets get larger, t-intervals look
| normal. We'll cover the one- and two-group versions which depend on the data you
| have.

...

  |========                                                                      |  11%
| The t distribution, invented by William Gosset in 1908, has thicker tails than the
| normal. Also, instead of having two parameters, mean and variance, as the normal
| does, the t distribution has only one - the number of degrees of freedom (df).

...

  |=========                                                                     |  12%
| As df increases, the t distribution gets more like a standard normal, so it's
| centered around 0. Also, the t assumes that the underlying data are iid Gaussian so
| the statistic (X' - mu)/(s/sqrt(n)) has n-1 degrees of freedom.

...

  |==========                                                                    |  13%
| Quick check. In the formula t=(X' - mu)/(s/sqrt(n)), if we replaced s by sigma the
| statistic t would be what asymptotically?.

1: Huh?
2: the population variance
3: the standard abnormal
4: the standard normal

Selection: 4

| Perseverance, that's the answer.

  |===========                                                                   |  14%
| To see what we mean, we've taken code from the slides, the function myplot, which
| takes the integer df as its input and plots the t distribution with df degrees of
| freedom. It also plots a standard normal distribution so you can see how they relate
| to one another.

...

  |============                                                                  |  16%
| Try myplot now with an input of 2.

> myplot(2)

| Nice work!

  |=============                                                                 |  17%
| You can see that the hump of t distribution (in blue) is not as high as the
| normal's. Consequently, the two tails of the t distribution absorb the extra mass,
| so they're thicker than the normal's. Note that with 2 degrees of freedom, you
| only have 3 data points. Ha! Talk about small sample sizes. Now try myplot with an
| input of 20.

> myplot(20)

| That's a job well done!

  |==============                                                                |  18%
| The two distributions are almost right on top of each other using this higher
| degree of freedom.

...

  |===============                                                               |  20%
| Another way to look at these distributions is to plot their quantiles. From the
| slides, we've provided a second function for you, myplot2, which does this. It
| plots a lightblue reference line representing normal quantiles and a black line
| for the t quantiles. Both plot the quantiles starting at the 50th percentile which
| is 0 (since the distributions are symmetric about 0) and go to the 99th.

...

  |================                                                              |  21%
| Try myplot2 now with an argument of 2.

> myplot(2)

| That's not the answer I was looking for, but try again. Or, type info() for more
| options.

| Type myplot2(2) at the command prompt.

> myplot2(2)

| Great job!

  |=================                                                             |  22%
| The distance between the two thick lines represents the difference in sizes
| between the quantiles and hence the two sets of intervals. Note the thin
| horizontal and vertical lines. These represent the .975 quantiles for the t and
| normal distributions respectively. Anyway, you probably recognized the placement
| of the vertical at 1.96 from the Asymptotics lesson.

...

  |==================                                                            |  24%
| Check the placement of the horizontal now using the R function qt with the
| arguments .975 for the quantile and 2 for the degrees of freedom (df).

> qt(.975, 2)
[1] 4.302653

| You are quite good my friend!

  |====================                                                          |  25%
| See? It matches the horizontal line of the plot. Now run myplot2 with an argument
| of 20.

> myplot2(20)

| You are amazing!

  |=====================                                                         |  26%
| The quantiles are much closer together with the higher degrees of freedom. At the
| 97.5 percentile, though, the t quantile is still greater than the normal.
| Student's Rules!

...

  |======================                                                        |  28%
| This means the the t interval is always wider than the normal. This is because
| estimating the standard deviation introduces more uncertainty so a wider interval
| results.

...

  |=======================                                                       |  29%
| So the t-interval is defined as X' +/- t_(n-1)*s/sqrt(n) where t_(n-1) is the
| relevant quantile. The t interval assumes that the data are iid normal, though it
| is robust to this assumption and works well whenever the distribution of the data
| is roughly symmetric and mound shaped.

...

  |========================                                                      |  30%
| Our plots showed us that for large degrees of freedom, t quantiles become close to
| what?

1: standard normal quantiles
2: very large numbers
3: standard abnormal quantiles
4: very small numbers

Selection: 1

| All that practice is paying off!

  |=========================                                                     |  32%
| Although it's pretty great, the t interval isn't always applicable. For skewed
| distributions, the spirit of the t interval assumptions (being centered around 0)
| are violated. There are ways of working around this problem (such as taking logs
| or using a different summary like the median).

...

  |==========================                                                    |  33%
| For highly discrete data, like binary, intervals other than the t are available.

...

  |===========================                                                   |  34%
| However, paired observations are often analyzed using the t interval by taking
| differences between the observations. We'll show you what we mean now.

...

  |============================                                                  |  36%
| We hope you're not tired because we're going to look at some sleep data. This was
| the data originally analyzed in Gosset's Biometrika paper, which shows the
| increase in hours for 10 patients on two soporific drugs.

...

  |=============================                                                 |  37%
| We've loaded the data for you. R treats it as two groups rather than paired. To
| see what we mean type sleep now. This will show you how the data is stored.

> sleep
   extra group ID
1    0.7     1  1
2   -1.6     1  2
3   -0.2     1  3
4   -1.2     1  4
5   -0.1     1  5
6    3.4     1  6
7    3.7     1  7
8    0.8     1  8
9    0.0     1  9
10   2.0     1 10
11   1.9     2  1
12   0.8     2  2
13   1.1     2  3
14   0.1     2  4
15  -0.1     2  5
16   4.4     2  6
17   5.5     2  7
18   1.6     2  8
19   4.6     2  9
20   3.4     2 10

| You got it!

  |==============================                                                |  38%
| We see 20 entries, the first 10 show the results (extra) of the first drug (group
| 1) on each of the patients (ID), and the last 10 entries the results of the second
| drug (group 2) on each patient (ID).

...

  |===============================                                               |  39%
| Here we've plotted the data in a paired way, connecting each patient's two results
| with a line, group 1 results on the left and group 2 on the right. See that purple
| line with the steep slope? That's ID 9, with 0 result for group 1 and 4.6 for
| group 2.

...

  |================================                                              |  41%
| If we just looked at the 20 data points we'd be comparing group 1 variations with
| group 2 variations. Both groups have quite large ranges. However, when we look at
| the data paired for each patient, we see that the variations in results are
| usually much smaller and depend on the particular subject.

...

  |=================================                                             |  42%
| To clarify, we've defined some variables for you, namely g1 and g2. These are two
| 10-long vectors, respectively holding the results of the 10 patients for each of
| the two drugs. Look at the range of g1 using the R command range.

> range(r1)
Error: object 'r1' not found
> range(g1)
[1] -1.6  3.7

| That's the answer I was looking for.

  |==================================                                            |  43%
| So g1 values go from -1.6 to 3.7. Now look at the range of g2. We see that the
| ranges of both groups are relatively large.

> range(g2)
[1] -0.1  5.5

| All that hard work is paying off!

  |===================================                                           |  45%
| Now let's look at the pairwise difference. We can take advantage of R's
| componentwise subtraction of vectors and create the vector of difference by
| subtracting g1 from g2. Do this now and put the result in the variable difference.

> difference <- g2 - g1

| You nailed it! Good job!

  |====================================                                          |  46%
| Now use the R function mean to find the average of difference.

> mean(difference)
[1] 1.58

| All that practice is paying off!

  |=====================================                                         |  47%
| See how much smaller the mean difference in this paired data is compared to the
| group variations?

...

  |======================================                                        |  49%
| Now use the R function sd to find the standard deviation of difference and put the
| result in the variable s.

> s <- sd(difference)

| Nice work!

  |=======================================                                       |  50%
| Now recall the formula for finding the t confidence interval, X' +/-
| t_(n-1)*s/sqrt(n). Make the appropriate substitutions to find the 95% confidence
| intervals for the average difference you just computed. We've stored that average
| difference in the variable mn for you to use here. Remember to use the R construct
| c(-1,1) for the +/- portion of the formula and the R function qt with .975 and n-1
| degrees of freedom for the quantile portion. Our data size is 10.

> mn + c(-1, 1) * qt(.975, 9) * (s / sqrt(10))
[1] 0.7001142 2.4598858

| Not quite! Try again. Or, type info() for more options.

| Type mn + c(-1,1)*qt(.975,9)*s/sqrt(10) at the command prompt.

> mn + c(-1, 1) * qt(.975, 9) * s / sqrt(10)
[1] 0.7001142 2.4598858

| You got it right!

  |========================================                                      |  51%
| This says that with probability .95 the average difference of effects (between the
| two drugs) for an individual patient is between .7 and 2.46 additional hours of
| sleep.

...

  |=========================================                                     |  53%
| We could also just have used the R function t.test with the argument difference to
| get this result. (You can use the default values for all the other arguments.) As
| with the other R test functions, this returns a lot of information. Since all
| we're interested in at the moment is the confidence interval we can pick this off
| with the construct x$conf.int. Try this now.

> t.test(difference)$conf.int
[1] 0.7001142 2.4598858
attr(,"conf.level")
[1] 0.95

| Excellent job!

  |==========================================                                    |  54%
| Here's code from the slides which shows four different ways of using t.test
| (including the two we just went through) to find the confidence interval of this
| data. The code also shows how to display the intervals nicely in a 4 x 2 array.

...

  |===========================================                                   |  55%
| We now present methods, using t confidence intervals, for comparing independent
| groups.

...

  |============================================                                  |  57%
| Suppose that we want to compare the mean blood pressure between two groups in a
| randomized trial. We'll compare those who received the treatment to those who
| received a placebo. Unlike the sleep study, we cannot use the paired t test
| because the groups are independent and may have different sample sizes.

...

  |=============================================                                 |  58%
| So our goal is to find a 95% confidence interval of the difference between two
| population means. Let's represent this difference as mu_y - mu_x. How do we do
| this? Recall our formula X' +/- t_(n-1)*s/sqrt(n).

...

  |==============================================                                |  59%
| First we need a sample mean, but we have two, X' and Y', one from each group. It
| makes sense that we'd have to take their difference (Y'-X') as well, since we're
| looking for a confidence interval that contains the difference mu_y-mu_x. Now we
| need to specify a t quantile. Suppose the groups have different sizes n_x and n_y.

...

  |===============================================                               |  61%
| For one group we used the quantile t_(.975,n-1). What do you think we'll use for
| the quantile of this problem?

1: t_(.975,n_x-1)
2: t_(.975,n_y-n_x-2)
3: t_(.975,n_x+n_y-2)
4: t_(.975,n_x+n_y-1)

Selection: 3

| You are amazing!

  |================================================                              |  62%
| The only term remaining is the standard error which for the single group is
| s/sqrt(n). Let's deal with the numerator first. Our interval will assume (for now)
| a common variance s^2 across the two groups. We'll actually pool variance
| information from the two groups using a weighted sum. (We'll deal with the more
| complicated situation later.)

...

  |=================================================                             |  63%
| We call the variance estimator we use the pooled variance. The formula for it
| requires two variance estimators (in the form of the standard deviation), S_x and
| S_y, one for each group. We multiply each by its respective degrees of freedom and
| divide the sum by the total number of degrees of freedom. This weights the
| respective variances; those coming from bigger samples get more weight.

...

  |==================================================                            |  64%
| Which of the following represents the numerator of this expression?

1: (n_x-1)(S_x)^2+(n_y-1)(S_y)^2
2: (n_x)(S_x)+(n_y)(S_y)
3: (n_x)(S_x)^2+(n_y)(S_y)^2

Selection: 1

| Excellent job!

  |===================================================                           |  66%
| Which of the following represents the total number of degrees of freedom?

1: (n_x+n_y-1)
2: (n_x+n_y)
3: (n_x+n_y+2)
4: (n_x-1)+(n_y-1)

Selection: 4

| Nice work!

  |====================================================                          |  67%
| Now recall we're calculating the standard error term which for the single group
| case was s/sqrt(n). We've got the numerator done, by pooling the sample variances.
| How do we handle the 1/sqrt(n) portion? We can simply add 1/n_x and 1/n_y and take
| the square root of the sum. Then we MULTIPLY this by the sample variance to
| complete the estimate of the standard error.

...

  |=====================================================                         |  68%
| Now we'll plug in some numbers from the slides based on an example from Rosner's
| book Fundamentals of Biostatistics, a very good, if heavy, reference book. We want
| to compare blood pressure from two independent groups.

...

  |======================================================                        |  70%
| The first is a group of 8 oral contraceptive users and the second is a group of 21
| controls. The two means are X'_{oc}=132.86 and X'_{c}=127.44, and the two sample
| standard deviations are s_{oc}= 15.34 and s_{c}= 18.23. Let's first compute the
| numerator of the pooled sample variance by weighting the sum of the two by their
| respective sample sizes. Recall the formula (n_x-1)(S_x)^2+(n_y-1)(S_y)^2 and fill
| in the values to create a variable sp.

> sp <- (8-1)*15.34^2 + (21-1)*18.23^2

| That's not the expression I expected but it works.

| I've executed the correct expression in case the result is
| needed in an upcoming question.

| You are really on a roll!

  |=======================================================                       |  71%
| Now how many degrees of freedom are there? Put your answer
| in the variable ns.

> ns <- 21+8-2

| That's not the expression I expected but it works.

| I've executed the correct expression in case the result is
| needed in an upcoming question.

| All that hard work is paying off!

  |========================================================                      |  72%
| Now divide sp by ns, take the square root and put the
| result back in sp.

> sp <- sqrt(sp / ns)

| You got it!

  |=========================================================                     |  74%
| Now to find the 95% confidence interval. Recall our basic
| formula X' +/- t_(n-1)*s/sqrt(n) and all the changes we
| need to make for working with two independent samples.
| We'll plug in the difference of the sample means for X'
| and our variable ns for the degrees of freedom when
| finding the t quantile. For the standard error, we
| multiply sp by the square root of the sum 1/n_{oc} +
| 1/n_{c}. The values for this problem are X'_{oc}=132.86
| and X'_{c}=127.44, n_{oc}=8 and n_{c}=21. Be sure to use
| the R construct c(-1,1) for the +/- portion and the R
| function qt with the correct percentile and degrees of
| freedom.

> 132.86 - 127.44 +c(-1, 1) * qt(0.975, 27) * sp * sqrt(1/21 + 1/8)
[1] -9.521097 20.361097

| Not quite, but you're learning! Try again. Or, type info()
| for more options.

| Type 132.86-127.44+c(-1,1)*qt(.975,ns)*sp*sqrt(1/8+1/21)
| at the command prompt.

> not quite my ass
Error: unexpected symbol in "not quite"
> 132.86 - 127.44 +c(-1, 1) * qt(0.975, ns) * sp * sqrt(1/21 + 1/8)
[1] -9.521097 20.361097

| Almost! Try again. Or, type info() for more options.

| Type 132.86-127.44+c(-1,1)*qt(.975,ns)*sp*sqrt(1/8+1/21)
| at the command prompt.

> 132.86 - 127.44 +c(-1, 1) * qt(0.975, ns) * sp * sqrt(1/8 + 1/21)
[1] -9.521097 20.361097

| You are really on a roll!

  |==========================================================                    |  75%
| Notice that 0 is contained in this 95% interval. That
| means that you can't rule out that the means of the two
| groups are equal since a difference of 0 is in the
| interval.

...

  |============================================================                  |  76%
| Getting tired? Let's revisit the sleep problem and instead
| of looking at the data as paired over 10 subjects we'll
| look at it as two independent sets each of size 10. Recall
| the data is stored in the two vectors g1 and g2; we've
| also stored the difference between their means in the
| variable md.

...

  |=============================================================                 |  78%
| Let's compute the sample pooled variance and store it in
| the variable sp. Recall that this is the sqrt(weighted
| sums of sample variances/deg of freedom). The weight of
| each is the sample size-1. Use the R function var to
| compute the variances of g1 and g2. The degrees of freedom
| is 10+10-2 = 18.

> sp <- (9 * var(g1) + 9 * var(g2) ) / 18

| Not quite, but you're learning! Try again. Or, type info()
| for more options.

| Type sp <- sqrt((9*var(g1)+9*var(g2))/18) at the command
| prompt.

> sp <- sqrt((9 * var(g1) + 9 * var(g2) ) / 18)

| Perseverance, that's the answer.

  |==============================================================                |  79%
| Now the last term of the formula, the standard error of
| the mean difference, is simply sp times the square root of
| the sum 1/10 + 1/10. Find the 95% t confidence interval of
| the mean difference of the two groups g1 and g2.
| Substitute md and sp into the formula you used above.

> md + c(-1, 1) * qt(0.975, 18) * sp * sqrt(2/10)
[1] -0.203874  3.363874

| Not quite, but you're learning! Try again. Or, type info()
| for more options.

| Type md + c(-1,1)*qt(.975,18)*sp*sqrt(1/5) at the command
| prompt.

> md + c(-1, 1) * qt(0.975, 18) * sp * sqrt(1/5)
[1] -0.203874  3.363874

| That's correct!

  |===============================================================               |  80%
| We can check this manual calculation against the R
| function t.test. Since we subtracted g1 from g2, be sure
| to place g2 as your first argument and g1 as your second.
| Also make sure the argument paired is FALSE and var.equal
| is TRUE. We only need the confidence interval so use the
| construct x$conf.  Do this now.

> t.test(g2 - g1, paired=FALSE, var.equal=TRUE)$conf
[1] 0.7001142 2.4598858
attr(,"conf.level")
[1] 0.95

| That's not the answer I was looking for, but try again.
| Or, type info() for more options.

| Type t.test(g2,g1,paired=FALSE,var.equal=TRUE)$conf at the
| command prompt.

> t.test(g2, g1, paired=FALSE, var.equal=TRUE)$conf
[1] -0.203874  3.363874
attr(,"conf.level")
[1] 0.95

| Excellent job!

  |================================================================              |  82%
| Pretty cool that it matches, right? Note that 0 is again
| in this 95% interval so you can't reject the claim that
| the two groups are the same. (Recall that this is the
| opposite of what we saw with paired data.) Let's run
| t.test again, this time with paired=TRUE and see how
| different the result is. Don't specify var.equal and look
| only at the confidence interval.

> t.test(g2, g1, paired=TRUE)$conf
[1] 0.7001142 2.4598858
attr(,"conf.level")
[1] 0.95

| You got it right!

  |=================================================================             |  83%
| Just as we saw when we ran t.test on our vector,
| difference! See how the interval excludes 0? This means
| the groups when paired have much different averages.

...

  |==================================================================            |  84%
| Now let's talk about calculating confidence intervals for
| two groups which have unequal variances. We won't be
| pooling them as we did before.

...

  |===================================================================           |  86%
| In this case the formula for the interval is similar to
| what we saw before, Y'-X' +/- t_df * SE, where as before
| Y'-X' represents the difference of the sample means.
| However, the standard error SE and the quantile t_df are
| calculated differently from previous methods. Here SE is
| the square root of the sum of the squared standard errors
| of the two means, (s_1)^2/n_1 + (s_2)^2/n_2 .

...

  |====================================================================          |  87%
| When the underlying X and Y data are iid normal and the
| variances are different, the normalized statistic we started
| this lesson with, (X'-mu)/(s/sqrt(n)), doesn't follow a t
| distribution. However, it can be approximated by a t
| distribution if we set the degrees of freedom appropriately.

...

  |=====================================================================         |  88%
| The formula for the degrees of freedom is a complicated fraction
| that no one remembers.  The numerator is the SQUARE of the sum
| of the squared standard errors of the two sample means. Each has
| the form s^2/n. The denominator is the sum of two terms, one for
| each group. Each term has the same form. It is the standard
| error of the mean raised to the fourth power divided by the
| sample size-1. More precisely, each term looks like
| (s^4/n^2)/(n-1). We use this df to find the t quantile.

...

  |======================================================================        |  89%
| Here's the formula. You might have to stretch the plot window to
| get it displayed more clearly.

...

  |=======================================================================       |  91%
| Let's plug in the numbers from the blood pressure study to see
| how this works. Recall we have two groups, the first with size 8
| and X'_{oc}=132.86 and s_{oc}=15.34 and the second with size 21
| and X'_{c}=127.44 and s_{c}=18.23.

...

  |========================================================================      |  92%
| Let's compute the degrees of freedom first. Start with the numerator. It's the
| square of the sum of two terms. Each term is of the form s^2/n. Do this now and
| put the result in num. Our numbers were 15.34 with size 8 and 18.23 with size 21.

> num <- (18.23^2/21 + 15.34^2/8)^2

| That's not the expression I expected but it works.

| I've executed the correct expression in case the result is needed in an upcoming
| question.

| That's correct!

  |=========================================================================     |  93%
| Now the denominator. This is the sum of two terms. Each term has the form
| s^4/n^2/(n-1). These look a little different than the form displayed but they're
| equivalent. Put the result in the variable den. Our numbers were 15.34 with size 8
| and 18.23 with size 21.

> den <- (18.23^2/21)^2/20 + (15.34^2/8)^2/7

| That's not the expression I expected but it works.

| I've executed the correct expression in case the result is needed in an upcoming
| question.

| You are doing so well!

  |==========================================================================    |  95%
| Now divide num by den and put the result in mydf.

> mydf <- num/den

| Excellent work!

  |===========================================================================   |  96%
| Now with the R function qt(.975,mydf) compute the 95% t interval. Recall the
| formula. X'_{oc}-X'_{c} +/- t_df * SE. Recall that SE is the square root of the
| sum of the squared standard errors of the two means, (s_1)^2/n_1 + (s_2)^2/n_2 .
| Again our numbers are the following. X'_{oc}=132.86 s_{oc}=15.34 and n_{oc}=8 .
| X'_{c}=127.44 s_{c}=18.23 and n_{c}=21.

> 132.86 - 127.44 + c(-1, 1) * qt(0.975, mydf) * sqrt(18.23^2/21 + 15.34^2/8)
[1] -8.913327 19.753327

| That's not exactly what I'm looking for. Try again. Or, type info() for more
| options.

| Type 132.86-127.44 +c(-1,1)*qt(.975,mydf)*sqrt(15.34^2/8 + 18.23^2/21) at the
| command prompt.

> 132.86 - 127.44 + c(-1, 1) * qt(0.975, mydf) * sqrt(15.34^2/8 + 18.23^2/21)
[1] -8.913327 19.753327

| Keep up the great work!

  |============================================================================  |  97%
| Don't worry about these nasty calculations. R makes things a lot easier. If you
| call t.test with var.equal set to FALSE, then R calculates the degrees of freedom
| for you. You don't have to memorize the formula.

...

  |============================================================================= |  99%
| Congrats! You've concluded this rather t-dious lesson on all things t related -
| statistics, distributions, intervals. Hope you're not too teed off!

...

  |==============================================================================| 100%
| Would you like to receive credit for completing this course on Coursera.org?


---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------

Selection: 10

| Attempting to load lesson dependencies...

| Package ‘ggplot2’ loaded correctly!

  |                                                                           |   0%

| Hypothesis_Testing. (Slides for this and other Data Science courses may be found
| at github https://github.com/DataScienceSpecialization/courses/. If you care to
| use them, they must be downloaded as a zip file and viewed locally. This lesson
| corresponds to 06_Statistical_Inference/09_HT.)

...

  |=                                                                          |   1%
| In this lesson, as the name suggests, we'll discuss hypothesis testing which is
| concerned with making decisions about populations using observed data.

...

  |==                                                                         |   2%
| An important concept in hypothesis testing is the NULL hypothesis, usually denoted
| as H_0. This is the hypothesis that represents the status_quo and is assumed true.
| It's a baseline against which you're testing alternative hypotheses, usually
| denoted by H_a. Statistical evidence is required to reject H_0 in favor of the
| research or alternative hypothesis.

...

  |===                                                                        |   4%
| We'll consider the motivating example from the slides. A respiratory
| disturbance index (RDI) of more than 30 events / hour is considered
| evidence of severe sleep disordered breathing (SDB). Suppose that in a
| sample of 100 overweight subjects with other risk factors for SDB at a
| sleep clinic, the mean RDI (X') was 32 events / hour with a standard
| deviation (s) of 10 events / hour.

...

  |====                                                                       |   5%
| We want to test the null hypothesis H_0 that mu = 30. Our alternative
| hypothesis H_a is mu>30. Here mu represents the hypothesized population
| mean RDI.

...

  |=====                                                                      |   6%
| So we have two competing hypotheses, H_0 and H_a, of which we'll have to
| pick one (using statistical evidence). That means we have four possible
| outcomes determined by what really is (the truth) and which hypothesis we
| accept based on our data. Two of the outcomes are correct and two are
| errors.

...

  |=====                                                                      |   7%
| Which of the following outcomes would be correct?

1: H_a is TRUE and we accept it
2: H_0 is FALSE and we accept it
3: H_a is FALSE and we accept it
4: H_0 is TRUE and we reject it

Selection: 1

| Nice work!

  |======                                                                     |   8%
| Which of the following outcomes would be an error?

1: H_a is FALSE and we reject it
2: H_a is TRUE and we accept it
3: H_0 is TRUE and we reject it
4: H_0 is FALSE and we reject it

Selection: 4

| Not quite, but you're learning! Try again.

| It's always a mistake to REJECT the TRUTH.

1: H_0 is TRUE and we reject it
2: H_a is FALSE and we reject it
3: H_a is TRUE and we accept it
4: H_0 is FALSE and we reject it

Selection: 3

| Try again. Getting it right on the first try is boring anyway!

| It's always a mistake to REJECT the TRUTH.

1: H_a is FALSE and we reject it
2: H_0 is TRUE and we reject it
3: H_a is TRUE and we accept it
4: H_0 is FALSE and we reject it

Selection: 2

| Perseverance, that's the answer.

  |=======                                                                    |  10%
| So it's correct to accept a true hypothesis or reject a false one. Pretty
| clear, right?

...

  |========                                                                   |  11%
| The errors are also clear - rejecting a true hypothesis or accepting a
| false one.

...

  |=========                                                                  |  12%
| We distinguish between these two errors. A Type I error REJECTS a TRUE
| null hypothesis H_0 and a Type II error ACCEPTS a FALSE null hypothesis
| H_0.

...

  |==========                                                                 |  13%
| Can we ever be sure that we're absolutely right?

1: Always
2: Let's not get into philosophy now
3: Yes
4: No

Selection: 4

| Your dedication is inspiring!

  |===========                                                                |  14%
| Since there's some element of uncertainty in questions concerning
| populations, we deal with probabilities. In our hypothesis testing we'll
| set the probability of making errors small. For now we'll focus on Type I
| errors, rejecting a correct hypothesis.

...

  |============                                                               |  16%
| The probabilities of making these two kinds of errors are related. If you
| decrease the probability of making a Type I error (rejecting a true
| hypothesis), you increase the probability of making a Type II error
| (accepting a false one) and vice versa.

...

  |=============                                                              |  17%
| As in the slides, we'll consider an American court of law. The null
| hypothesis is that the defendant is innocent. If an innocent man is
| convicted what type of error is this?

1: Type I
2: Type II

Selection: 1

| Perseverance, that's the answer.

  |==============                                                             |  18%
| You might send the innocent man to jail by rejecting H_0. Suppose a guilty
| person is not convicted. What type of error is this?

1: Type I
2: Type II

Selection: 2

| All that hard work is paying off!

  |==============                                                             |  19%
| Back to sleep (example)! A reasonable strategy would reject the null
| hypothesis if our sample mean X' was larger than some constant C. We
| choose C so that the probability of a Type I error, alpha, is .05 (or some
| other favorite constant). Many scientific papers use .05 as a standard
| level of rejection.

...

  |===============                                                            |  20%
| This means that alpha, the Type I error rate, is the probability of
| rejecting the null hypothesis when, in fact, it is correct. We don't want
| alpha too low because then we would never reject the null hypothesis even
| if it's false.

...

  |================                                                           |  22%
| Recall that the standard error of a sample mean is given by the formula
| s/sqrt(n). Recall in our sleep example we had a sample of 100 subjects,
| our mean RDI (X') was 32 events / hour with a standard deviation (s) of 10
| events / hour. What is the standard error of the mean in this example?

> 1
[1] 1

| Perseverance, that's the answer.

  |=================                                                          |  23%
| Under H_0, X' is normally distributed with mean mu=30 and variance 1.
| (We're estimating the variance as the square of the standard error which
| in this case is 1.) We want to choose the constant C so that the
| probability that X is greater than C given H_0 is 5%. That is, P(X > C|
| H_0) is 5%. Sound familiar?

...

  |==================                                                         |  24%
| Here's a plot to show what we mean. The shaded portion represents 5% of
| the area under the curve and those X values in it are those for which the
| probability that X>C is 5%.

...

  |===================                                                        |  25%
| The shaded portion represents 5% of the area under this normal density
| curve. Which expression represents the smallest value X for which the area
| is shaded, assuming this is standard normal?

1: qt(.95,99)
2: qnorm(.95)
3: dnorm(.95)
4: rnorm(.95)

Selection: 2

| Excellent job!

  |====================                                                       |  27%
| The 95th percentile of a standard normal distribution is 1.645 standard
| deviations from the mean, so in our example we have to set C to be 1.645
| standard deviations MORE than our hypothesized mean of 30, that is, C = 30
| + 1.645 * 1 = 31.645 (recall that the variance and standard deviation
| equalled 1).

...

  |=====================                                                      |  28%
| This means that if our OBSERVED (sample) mean X' >= C, then it's only a 5%
| chance that a random draw from this N(30,1) distribution is larger than C.

...

  |======================                                                     |  29%
| Recall that our observed mean X' is 32 which is greater than C=31.645, so
| it falls in that 5% region. What do we do with H_0?

1: give it another chance
2: fail to reject it
3: reject it

Selection: 3

| Keep working like that and you'll get there!

  |=======================                                                    |  30%
| So the rule "Reject H_0 when the sample mean X' >= 31.645" has the
| property that the probability of rejecting H_0 when it is TRUE is 5% given
| the model of this example - hypothesized mean mu=30, variance=1 and n=100.

...

  |=======================                                                    |  31%
| Instead of computing a constant C as a cutpoint for accepting or rejecting
| the null hypothesis, we can simply compute a Z score, the number of
| standard deviations the sample mean is from the hypothesized mean. We can
| then compare it to quantile determined by alpha.

...

  |========================                                                   |  33%
| How do we do this? Compute the distance between the two means (32-30) and
| divide by the standard error of the mean, that is (s/sqrt(n)).

...

  |=========================                                                  |  34%
| What is the Z score for this example? Recall the Z score is X'-mu divided
| by the standard error of the mean. In this example X'=32, mu=30 and the
| standard error is 10/sqrt(100)=1.

> 2
[1] 2

| You're the best!

  |==========================                                                 |  35%
| The Z score is 2. The quantile is 1.645, so since 2>1.645. What do we do
| with H_0?

1: reject it
2: give it another chance
3: fail to reject it

Selection: 1

| Nice work!

  |===========================                                                |  36%
| The general rule for rejection is if sqrt(n) * ( X' - mu) / s >
| Z_{1-alpha}.

...

  |============================                                               |  37%
| Our test statistic is (X'-mu) / (s/sqrt(n)) which is standard normal.

...

  |=============================                                              |  39%
| This means that our test statistic has what mean and standard deviation?

1: 1 and 1
2: 0 and 1
3: 0 and 0
4: 1 and 0

Selection: 2

| You are doing so well!

  |==============================                                             |  40%
| Let's review and expand. Our null hypothesis is that the population mean
| mu equals the value mu_0 and alpha=.05. (This is the probability that we
| reject H_0 if it's true.) We can have several different alternative
| hypotheses.

...

  |===============================                                            |  41%
| Suppose our first alternative, H_a, is that mu < mu_0. We would reject H_0
| (and accept H_a) when our observed sample mean is significantly less than
| mu_0. That is, our test statistic (X'-mu) / (s/sqrt(n)) is less than
| Z_alpha. Specifically, it is more than 1.64 standard deviations to the
| left of the mean mu_0.

...

  |================================                                           |  42%
| Here's a plot to show what we mean. The shaded portion represents 5% of
| the area under the curve and those X values in it are those which are at
| least 1.64 standard deviations less than the mean. The probability of this
| is 5%. This means that if our sample mean fell in this area, we would
| reject a true null hypothesis, mu=mu_0, with probability 5%.

...

  |=================================                                          |  43%
| We already covered the alternative hypothesis H_a that mu > mu_0 but let's
| review it. We would reject H_0 (and accept H_a) when our sample mean is
| what?

1: equal to mu_0
2: significantly less than mu_0
3: huh?
4: significantly greater than mu_0

Selection: 4

| You got it right!

  |=================================                                          |  45%
| This means that our test statistic (X'-mu) / (s/sqrt(n)) is what?

1: equal to mu_0
2: huh?
3: at least 1.64 std dev less than mu_0
4: at least 1.64 std dev greater than mu_0

Selection: 4

| You nailed it! Good job!

  |==================================                                         |  46%
| Here again is the plot to show this. The shaded portion represents 5% of
| the area under the curve and those X values in it are those which are at
| least 1.64 standard deviations greater than the mean. The probability of
| this is 5%. This means that if our observed mean fell in this area we
| would reject a true null hypothesis, that mu=mu_0, with probability 5%.

...

  |===================================                                        |  47%
| Finally, let's consider the alternative hypothesis H_a that mu is simply
| not equal to mu_0, the mean hypothesized by the null hypothesis H_0.  We
| would reject H_0 (and accept H_a) when our sample mean is significantly
| different than mu_0, that is, either less than OR greater than mu_0.

...

  |====================================                                       |  48%
| Since we want to stick with a 5% rejection rate, we divide it in half and
| consider values at both tails, at the .025 and the .975 percentiles.  This
| means that our test statistic (X'-mu) / (s/sqrt(n)) is less than .025,
| Z_(alpha/2), or greater than .975, Z_(1-alpha/2).

...

  |=====================================                                      |  49%
| Here's the plot. As before, the shaded portion represents the 5% of the
| area composing the region of rejection. This time, though, it's composed
| of two equal pieces, each containing 2.5% of the area under the curve. The
| X values in the shaded portions are values which are at least 1.96
| standard deviations away from the hypothesized mean.

...

  |======================================                                     |  51%
| Notice that if we reject H_0, either it was FALSE (and hence our model is
| wrong and we are correct to reject it) OR H_0 is TRUE and we have made an
| error (Type I). The probability of this is 5%.

...

  |=======================================                                    |  52%
| Since our tests were based on alpha, the probability of a Type I error, we
| say that we "fail to reject H_0" rather than we "accept H_0". If we fail
| to reject H_0, then H_0 could be true OR we just might not have enough
| data to reject it.

...

  |========================================                                   |  53%
| We have not fixed the probability of a type II error (accepting H_0 when
| it is false), which we call beta. The term POWER refers to the quantity
| 1-beta and it represents the probability of rejecting H_0 when it's false.
| This is used to determine appropriate sample sizes in experiments.

...

  |=========================================                                  |  54%
| What do you think we call the region of values for which we reject H_0?

1: the waggy tails
2: the abnormal region
3: the region of interest
4: the rejection region
5: the shady tails

Selection: 4

| You're the best!

  |==========================================                                 |  55%
| Note that so far we've been talking about NORMAL distributions and
| implicitly relying on the CENTRAL LIMIT THEOREM (CLT).

...

  |==========================================                                 |  57%
| Remember the CLT. For a distribution to be approximated by a normal what
| does the sample size have to be?

1: large
2: small
3: normal
4: abnormal

Selection: 1

| Nice work!

  |===========================================                                |  58%
| No need to worry. If we don't have a large sample size, we can use the t
| distribution which conveniently uses the same test statistic (X'-mu) /
| (s/sqrt(n)) we used above.  That means that all the examples we just went
| through would work exactly the same EXCEPT instead of using NORMAL
| quantiles, we would use t quantiles and n-1 degrees of freedom.

...

  |============================================                               |  59%
| We said t distributions were very handy, didn't we?

...

  |=============================================                              |  60%
| Let's go back to our sleep disorder example and suppose our sample size=16
| (instead of 100). As before, (sample mean) X'=32, (standard deviation)
| s=10.  H_0 says the true mean mu=30, and H_a is that mu>30. With this
| smaller sample size we use the t test, but our test statistic is computed
| the same way, namely (X'-mu)/(s/sqrt(n))

...

  |==============================================                             |  61%
| What is the value of the test statistic (X'-mu)/(s/sqrt(n)) with sample
| size 16?

> 2
[1] 2

| Keep trying! Or, type info() for more options.

| Type (32-30)/(10/4) at the command prompt.

> 2/(10/4)
[1] 0.8

| You are doing so well!

  |===============================================                            |  63%
| How many degrees of freedom do we have with a sample size of 16?

> 15
[1] 15

| That's correct!

  |================================================                           |  64%
| Under H_0, the probability that the test statistic is larger than the 95th
| percentile of the t distribution is 5%. Use the R function qt with the
| arguments .95 and the correct number of degrees of freedom to find the
| quantile.

> qt(0.95, 15)
[1] 1.75305

| You're the best!

  |=================================================                          |  65%
| So the test statistic (.8) is less than 1.75, the 95th percentile of the t
| distribution with 15 df. This means that our sample mean (32) does not
| fall within the region of rejection since H_a was that mu>30.

...

  |==================================================                         |  66%
| This means what?

1: we reject H_0
2: we reject H_a
3: we fail to reject H_0

Selection: 3

| Perseverance, that's the answer.

  |===================================================                        |  67%
| Now let's consider a two-sided test. Suppose that we would reject the null
| hypothesis if in fact the sample mean was too large or too small. That is,
| we want to test the alternative H_a that mu is not equal to 30. We will
| reject if the test statistic, 0.8, is either too large or too small.

...

  |====================================================                       |  69%
| As we discussed before, we want the probability of rejecting under the
| null to be 5%, split equally as 2.5% in the upper tail and 2.5% in the
| lower tail. Thus we reject if our test statistic is larger than qt(.975,
| 15) or smaller than qt(.025, 15).

...

  |====================================================                       |  70%
| Do you expect qt(.975,15) to be bigger or smaller than qt(.95,15)?

1: smaller
2: bigger

Selection: 2

| You got it right!

  |=====================================================                      |  71%
| Since the test statistic was smaller than qt(.95,15) will it be bigger or
| smaller than qt(.975,15)?

1: smaller
2: bigger

Selection: 1

| Keep up the great work!

  |======================================================                     |  72%
| Now for the left tail, qt(.025,15). What can we say about it?

1: we don't know anything about it
2: it is greater than 0
3: it is bigger than qt(.975,15)
4: it is less than 0

Selection: 4

| You're the best!

  |=======================================================                    |  73%
| Bottom line here is if you fail to reject the one sided test, you know
| that you will fail to reject the two sided.

...

  |========================================================                   |  75%
| So the test statistic .8 failed both sides of the test. That means we ?

1: huh?
2: reject H_a
3: reject H_0
4: fail to reject H_0

Selection: 4

| You are really on a roll!

  |=========================================================                  |  76%
| Now we usually don't have to do all this computation ourselves because R
| provides the function t.test which happily does all the work! To prove
| this, we've provided a csv file with the father_son height data from John
| Verzani's UsingR website (http://wiener.math.csi.cuny.edu/UsingR/) and
| read it into a data structure fs for you. We'll do a t test on this paired
| data to see if fathers and sons have similar heights (our null
| hypothesis).

...

  |==========================================================                 |  77%
| Look at the dimensions of fs now using the R function dim.

> dim(fs)
[1] 1078    2

| That's a job well done!

  |===========================================================                |  78%
| So fs has 1078 rows and 2 columns. The columns, fheight and sheight,
| contain the heights of a father and his son. Obviously there are 1078 such
| pairs. We can run t.test on this data in one of two ways. First, we can
| run it with just one argument, the difference between the heights, say
| fs$sheight-fs$fheight. OR we can run it with three arguments, the two
| heights plus the paired argument set to TRUE. Run t.test now using
| whichever way you prefer.

> t.test(fs$fheight, fs$sheight, paired = TRUE)

	Paired t-test

data:  fs$fheight and fs$sheight
t = -11.789, df = 1077, p-value < 2.2e-16
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 -1.1629160 -0.8310296
sample estimates:
mean of the differences 
             -0.9969728 


| You are really on a roll!

  |============================================================               |  80%
| The test statistic is what?

1: .8310296
2: 2.2e-16
3: 0.9969728
4: 11.7885

Selection: 4

| Excellent job!

  |=============================================================              |  81%
| So the test statistic is 11.79 which is quite large so we REJECT the null
| hypothesis that the true mean of the difference was 0 (if you ran the test
| on the difference sheight-fheight) or that the true difference in means
| was 0 (if you ran the test on the two separate but paired columns).

...

  |=============================================================              |  82%
| The test statistic tell us what?

1: the sample mean
2: the true mean
3: the number of estimated std errors between the sample and hypothesized means
4: the true variance

Selection: 3

| Great job!

  |==============================================================             |  83%
| We can test this by multiplying the t statistic (11.7885) by the standard
| deviation of the data divided by the square root of the sample size.
| Specifically run 11.7885 * sd(fs$sheight-fs$fheight)/sqrt(1078).

> 11.7885 * sd(fs$sheight - fs$fheight)/sqrt(1078)
[1] 0.9969686

| That's correct!

  |===============================================================            |  84%
| This should give you a close match to the mean of x which t.test gave you,
| 0.9969728.

...

  |================================================================           |  86%
| Note the 95% confidence interval, 0.8310296 1.1629160, returned by t.test.
| It does not contain the hypothesized population mean 0 so we're pretty
| confident we can safely reject the hypothesis. This tells us that either
| our hypothesis is wrong or we're making a mistake (Type 1) in rejecting
| it.

...

  |=================================================================          |  87%
| You've probably noticed the strong similarity between the confidence
| intervals we studied in the last lesson and these hypothesis tests. That's
| because they're equivalent!

...

  |==================================================================         |  88%
| If you set alpha to some value (say .05) and ran many tests checking
| alternative hypotheses against H_0, that mu=mu_0, the set of all possible
| values for which you fail to reject H_0 forms the (1-alpha)% (that is 95%)
| confidence interval for mu_0.

...

  |===================================================================        |  89%
| Similarly, if a (1-alpha)% interval contains mu_0, then we fail to reject
| H_0.

...

  |====================================================================       |  90%
| Let's see how hypothesis testing works with binomial distributions by
| considering the example from the slides. A family has 8 children, 7 of
| whom are girls and none are twins. Let the null hypothesis be that either
| gender is equally likely, like an iid coin flip.

...

  |=====================================================================      |  92%
| So our H_0 is that p=.5, where p is the probability of a girl. We want to
| see if we should reject H_0 based on this sample of size 8. Our H_a is
| that p>.5, so we'll do a one-sided test, i.e., look at only the right tail
| of the distribution.

...

  |======================================================================     |  93%
| Let's set alpha, the level of our test, to .05 and find the probabilities
| associated with different rejection regions, where a rejection region i
| has at least i-1 girls out of a possible 8.

...

  |======================================================================     |  94%
| We've defined for you a 9-long vector, mybin, which shows nine
| probabilities, the i-th of which is the probability that there are at
| least i-1 girls out of the 8 possible children. Look at mybin now.

> mybin
[1] 1.00000000 0.99609375 0.96484375 0.85546875 0.63671875 0.36328125
[7] 0.14453125 0.03515625 0.00390625

| Great job!

  |=======================================================================    |  95%
| So mybin[1]=1.0, meaning that with probability 1 there are at least 0
| girls, and mybin[2]=.996 is the probability that there's at least 1 girl
| out of the 8, and so forth. The probabilities decrease as i increases.
| What is the least value of i for which the probability is less than .05?

> mybin[-2]
[1] 1.00000000 0.96484375 0.85546875 0.63671875 0.36328125 0.14453125
[7] 0.03515625 0.00390625

| Try again. Getting it right on the first try is boring anyway! Or, type
| info() for more options.

| mybin[7]=.144 and mybin[8]=.035.

> mybin[7]
[1] 0.1445313

| Not quite! Try again. Or, type info() for more options.

| mybin[7]=.144 and mybin[8]=.035.

> mybin[8]
[1] 0.03515625

| Give it another try. Or, type info() for more options.

| mybin[7]=.144 and mybin[8]=.035.

> 7
[1] 7

| That's not exactly what I'm looking for. Try again. Or, type info() for
| more options.

| mybin[7]=.144 and mybin[8]=.035.

> 8
[1] 8

| Nice work!

  |========================================================================   |  96%
| So mybin[8]=.03 is the probability of having at least 7 girls out of a
| sample of size 8 under H_0 (if p actually is .5) which is what our sample
| has. This is less than .05 so our sample falls in this region of
| rejection. Does that mean we accept or reject H_0, (that either gender is
| equally likely) based on this sample of size 8?

1: reject H_0
2: accept H_0

Selection: 1

| Great job!

  |=========================================================================  |  98%
| Finally, we note that a 2-sided test would mean that our alternative
| hypothesis is that p is not equal to .5, and it's not obvious how to do
| this with a binomial distribution. Don't worry, though, because the next
| lesson on p-values will make this clearer. It's interesting that for
| discrete distributions such as binomial and Poisson, inverting 2-sided
| tests is how R calculates exact tests. (It doesn't rely on the CLT.)

...

  |========================================================================== |  99%
| Congrats! We confidently hypothesize that you're happy to have finished
| this lesson. Can we test this?

...

  |===========================================================================| 100%
| Would you like to receive credit for completing this course on
| Coursera.org?

1: No
2: Yes



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------


  |                                                                   |   0%

| P_Values. (Slides for this and other Data Science courses may be found at
| github https://github.com/DataScienceSpecialization/courses/. If you care
| to use them, they must be downloaded as a zip file and viewed locally.
| This lesson corresponds to 06_Statistical_Inference/10_pValues.)

...

  |==                                                                 |   2%
| In this lesson, as the name suggests, we'll discuss p-values which have nothing to do with urological
| testing. Instead they are the most common measure of statistical significance.

...

  |===                                                                |   5%
| However, because they're popular they're used a lot, and often they're misused or misinterpreted. In
| this lecture we'll focus on how to generate them and interpret them correctly.

...

  |=====                                                              |   7%
| The question motivating p-values is this. Given that we have some null hypothesis concerning our data
| (for example, its mean), how unusual or extreme is the sample value we get from our data? Is our test
| statistic consistent with our hypothesis? So there are, implicitly, three steps we have to take to
| answer these types of questions.

...

  |======                                                             |  10%
| What do you think the first step is?

1: Consult your crystal ball
2: Compare the test statistic to a Z or t quantile
3: Create a null hypothesis
4: Calculate a test statistic from the data

Selection: 3

| You are doing so well!

  |========                                                           |  12%
| So we have to begin with a null hypothesis which is a reasoned guess at some distribution of a data
| summary (a statistic). Recall from the last lesson that the null hypothesis H_0 is a baseline against
| which we'll measure an alternative hypothesis using the actual observed data.

...

  |==========                                                         |  14%
| So you propose a null hypothesis. What's the next step?

1: Go back to the crystal ball
2: Calculate a test statistic from the given data
3: Reject H_0
4: Compare the test statistic to a Z or t score

Selection: 2

| That's a job well done!

  |===========                                                        |  17%
| Now you have a proposed statistic (from your reasoned hypothesis) and a test statistic computed from
| your gathered data. What's the final step?

1: Compare the test statistic to the hypothetical distribution
2: Calculate a test statistic from the given data
3: Go back to the crystal ball
4: Reject H_0

Selection: 1

| All that hard work is paying off!

  |=============                                                      |  19%
| Your comparison tells you how "extreme" the test value is toward the alternative hypothesis. The
| p-value is the probability under the null hypothesis of obtaining evidence as or more extreme than
| your test statistic (obtained from your observed data) in the direction of the alternative hypothesis.

...

  |==============                                                     |  21%
| So if the p-value (probability of seeing your test statistic) is small, then one of two things
| happens. EITHER H_0 is true and you have observed a rare event (in this unusual test statistic) OR H_0
| is false. Let's go through an example.

...

  |================                                                   |  24%
| Suppose that you get a t statistic of 2.5 with 15 df testing H_0, (that mu = mu_0) versus an
| alternative H_a (that mu > mu_0). We want to find the probability of getting a t statistic as large as
| 2.5.

...

  |==================                                                 |  26%
| R can help us! We can use the R function pt, the distribution function of the t distribution. This
| function returns one of two probabilities, EITHER the probability of X > q (if lower.tail is FALSE) OR
| X <= q (if lower.tail is TRUE), where q is a quantile argument. Here we'll set q=2.5, df=15,
| lower.tail=FALSE since H_a says that mu>mu_0. We have to gauge the extremity in the direction of H_a.
| Run this now.

> pt(2.5, 15, lower.tail = FALSE)
[1] 0.0122529

| Perseverance, that's the answer.

  |===================                                                |  29%
| This result tells us that, if H_0 were true, we would see this large a test statistic with probability
| 1% which is rather a small probability.

...

  |=====================                                              |  31%
| What should we do?

1: Reject H_0
2: Consult the crystal ball
3: Fail to reject H_0

Selection: 1

| Your dedication is inspiring!

  |======================                                             |  33%
| Another way to think about a p-value is as an attained significance level. This is a fancy way of
| saying that the p-value is the smallest value of alpha at which you will reject the null hypothesis.

...

  |========================                                           |  36%
| Recall the example from our last lesson in which we computed a test statistic of 2. Our H_0 said that
| mu_0 = 30 and the alternative H_a that mu > 30. Assume we used a Z test (normal distribution). We
| rejected the one sided test when alpha was set to 0.05.

...

  |==========================                                         |  38%
| Why did we reject? Find the quantile associated with this test, that's the place to start. Use qnorm
| at the 95th percentile.

> qnorm(095)
[1] NaN
Warning message:
In qnorm(95) : NaNs produced

| You almost had it, but not quite. Try again. Or, type info() for more options.

| Type qnorm(.95) at the command prompt.

> qnorm(0.95)
[1] 1.644854

| Great job!

  |===========================                                        |  40%
| We rejected H_0 because our data (the test statistic actually) favored H_a. The test statistic 2
| (shown by the vertical blue line) falls in the shaded portion of this figure because it exceeds the
| quantile. As you know, the shaded portion represents 5% of the area under the curve.

...

  |=============================                                      |  43%
| Now try the 99th percentile to see if we would still reject H_0.

> qnorm(0.99)
[1] 2.326348

| Nice work!

  |==============================                                     |  45%
| Would we reject H_0 if alpha were .01?

1: Yes
2: No

Selection: 2

| Nice work!

  |================================                                   |  48%
| Again, a picture's worth a thousand words, right? The vertical line at the test statistic 2 is not in
| the region of rejection.

...

  |==================================                                 |  50%
| So our data (the test statistic) tells us what the attained significance level is. We use the R
| function pnorm to give us this number. With the default values, specifically lower.tail=TRUE, this
| gives us the probability that a random draw from the distribution is less than or equal to the
| argument. Try it now with the test statistic value 2. Use the default values for all the other
| arguments.

> pnorm(2)
[1] 0.9772499

| Your dedication is inspiring!

  |===================================                                |  52%
| Just as we thought, somewhere between .95 (where we rejected) and .99 (where we failed to reject).
| That's reassuring.

...

  |=====================================                              |  55%
| Now let's find the p value associated with this example. As before, we'll use pnorm. But this time
| we'll set the lower.tail argument to FALSE. This gives us the probability of X exceeding the test
| statistic, that is, the area under the curve to the right of test statistic. Try it now with the test
| statistic value 2.

> pnorm(2, lower.tail=FALSE)
[1] 0.02275013

| You are amazing!

  |======================================                             |  57%
| This tells us that the attained level of significance is about 2%.

...

  |========================================                           |  60%
| By reporting a p-value, instead of an alpha level and whether or not you reject H_0, reviewers of your
| work can hypothesis test at any alpha level they choose. The general rule is that if the p-value is
| less than the specified alpha you reject the null hypothesis and if it's greater you fail to reject.

...

  |=========================================                          |  62%
| For a two sided hypothesis test, you have to double the smaller of the two one-sided p values. We'll
| see an example of this shortly. Most software assumes a two-sided test and automatically doubles the p
| value.

...

  |===========================================                        |  64%
| Now for the two-sided test. Recall the binomial example from the last lesson - the family with 8
| children, 7 of whom are girls. You want to test H_0, that p=.5, where p is the probability of a girl
| (like a fair coin flip). H_a is that p is not equal to .5. It's either greater or less than .5.

...

  |=============================================                      |  67%
| This is a two-sided test. First we find the probability of having at least i girls, for i running from
| 0 to 8. We have a vector of these probabilities, mybin. Look at it now.

> mybin
[1] 1.00000000 0.99609375 0.96484375 0.85546875 0.63671875 0.36328125 0.14453125 0.03515625 0.00390625

| Perseverance, that's the answer.

  |==============================================                     |  69%
| The second last value shows us that the probability of having at least 7 girls (out of 8 children) is
| .035, assuming that genders are equally likely (p=.5).  You can verify this with the R function
| pbinom, with the arguments 6, size=8, prob=.5, and lower.tail=FALSE. (This last yields the probability
| that X>6.) Try this now.

> pbinom(6, 8, 0.5, lower.tail=FALSE)
[1] 0.03515625

| Your dedication is inspiring!

  |================================================                   |  71%
| We see a probability of about .03. Should we reject or fail to reject H_0 if alpha = .05?

1: Fail to reject
2: Reject

Selection: 2

| Excellent job!

  |=================================================                  |  74%
| We see a probability of about .03. Should we reject or fail to reject H_0 if alpha = .04?

1: Fail to reject
2: Reject

Selection: 2

| That's a job well done!

  |===================================================                |  76%
| We see a probability of about .03. Should we reject or fail to reject H_0 if alpha = .03?

1: Fail to reject
2: Reject

Selection: 1

| That's the answer I was looking for.

  |=====================================================              |  79%
| For the other side of the test we want the probability that X<=7, again out of a sample of size 8 with
| probability .5. Again, we use pbinom, this time with an argument of 7 and lower.tail=TRUE. Try this
| now.

> pbinom(7, 8, 0.5, lower.tail=TRUE)
[1] 0.9960938

| You are really on a roll!

  |======================================================             |  81%
| So it's pretty likely (probability .996) that out of 8 children you'll have at most 7 girls. The p
| value of this two sided test is 2*the smaller of the two one-sided values. In this case the lower
| value is .035, so 2*.035 is the p-value for this two-sided test.

...

  |========================================================           |  83%
| Now a final example using a Poisson distribution. Remember that this is discrete and it involves
| counts or rates of counts. The example from the slides involves rates of infections in a hospital.

...

  |=========================================================          |  86%
| Suppose that the hospital has an infection rate of 10 infections per 100 person/days at risk. This is
| a rate of 0.1.  Assume that an infection rate of 0.05 is the benchmark. This is our alpha level,
| recognize it? With this model, could the observed rate (.1) be larger than the benchmark 0.05 by
| chance or does it indicate a problem?

...

  |===========================================================        |  88%
| In other words, H_0 says that lambda = 0.05 so lambda_0 * 100 = 5, and H_a says that lambda > 0.05. Is
| H_0 true and our observed rate (.1) is just a fluke OR should we reject H_0 ?

...

  |=============================================================      |  90%
| As before, R has the handy function ppois, which returns probabilities for Poisson distributions. We
| want the probability of seeing at least 9 infections using a lambda value of 5 and lower.tail=FALSE.
| As when we used pbinom we have to use 9 as the argument since we're looking for a probability of a
| value greater than the argument. Try this now.

> ppois(9, 5, lower.tail=FALSE)
[1] 0.03182806

| You are really on a roll!

  |==============================================================     |  93%
| We see a probability of about .03. Should we reject or fail to reject H_0? (Remember those helpful
| pictures with shaded areas. Smaller areas mean smaller probabilities and vice versa.)

1: Fail to reject
2: Reject

Selection: 2

| That's the answer I was looking for.

  |================================================================   |  95%
| So we reject the infection rate hypothesized by H_0 since the data favors H_a, indicating that the
| rate is much higher.

...

  |=================================================================  |  98%
| Congrats! You finished this lesson. We hope you p-valued it.

...

  |===================================================================| 100%
| Would you like to receive credit for completing this course on Coursera.org?

1: Yes
2: No
