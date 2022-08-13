---
layout: page
title: R_random_posts
permalink: /r-random-post/
feature-img: "assets/img/pexels/travel.jpeg"
tags: [r-random-posts]
---
Here, I will list some random observations I got while using R. 

- [GitHub Cheat Sheet](https://tranktle.github.io/r-random-tricks/github-cheatsheet.html)

- [Some problems that we may cope with when using dplyr::full_join. These are why you may need powerchoice::power_full_join.](https://tranktle.github.io/r-random-tricks/problems-when-using-dplyrfull_join.html)

Assume that our data comes from MANY different tables, and we want to join these tables using people's IDs. It is essential to notice the assumption that each person has a **unique ID** so that we can use it as a **key** to join our tables. 

Some problems may arrive when we want to use `dplyr::full_join` to keep all the columns when our tables have duplicated column names. Even in the worst scenario, these duplicated columns have different values for some people due to data input mistakes or other reasons. In this case, even though we set up by= ID, the `dplyr::full_join` may still think that some people have identical IDs. Using `dplyr::full_join` will end up with a combined data set with some people's information appearing in many rows (and those information may not aggree with each other). 

In this case, `powerjoin::power_full_join` can be helpful to collect all of the information from one person to put them in just one row, and we can end up with a clean combined data table. 
