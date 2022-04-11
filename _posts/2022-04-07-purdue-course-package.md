---
title: Purdue Course PHP Package 
date: 2022-04-11 22:10
categories: [Projects, Packages]
tags: [projects, packages, php, laravel] 
---

![Purdue Course](https://camo.githubusercontent.com/d88def7104ee0b634843340685d766e6d7ce9e786cd383b01164b1c67b2685e7/687474703a2f2f692e696d6775722e636f6d2f513735597972722e706e67)

## Synopsis

10+ years have been already passed, since concept of **Software Development** became more like a stacking multiple blocks of package. According to the [npmjs official blog](https://blog.npmjs.org/post/615388323067854848/so-long-and-thanks-for-all-the-packages) (<u>no longer active</u>), the number of packages in npmjs alone is about **1.3 million** as of 2020. It is already 2022 today as I am writing this post with my coffee next to it, the number must be still on the rise.

This **PHP package** is one of many wrapper packages in the packagist that can be installed via composer dependency manager through [```dongyukang/purduecourse```](https://github.com/dongyukang/purduecourse).
I wrote this php library at 2017 (5 years ago from today) in hope for enhancing user experience by simplifying API query. Basically, ``` dongyukang/purduecourse``` is a wrapper package, it completely depends on [Purdue API](https://github.com/Purdue-io/PurdueApi), a restful api that allows users to get the Purdue University's course catalogs through OData queries. By utilizing this package, users are able to reduce repeating process of requesting data, parsing data, and all other time consuming tasks, and they can only focus on one major duty, retrieving Purdue course catalogs. This is the core objective to this project.  

## Brief introduction of the package

After installing and setup process is finished, retrieving Purdue course data becomes a pushover.
If user wants to retrieve all of informtion of a course name called 'CS 180' during fall semester of 2016, a single line of code can achieve a such job. 

```php
 Purdue::fall(2016)->course('cs 180')->all();
 ```

 The line above will result in:

 ![Result_Screen_Shot](https://camo.githubusercontent.com/184205886f373b8561c6e0bda1bbc7298cea5a9dfcec5bdd258577a5cabde1cb/687474703a2f2f692e696d6775722e636f6d2f624854493970332e706e67)

According to [Purdue API Entities Hierarchy](https://github.com/Purdue-io/PurdueApi/wiki/OData-Entities), 
the entity chaining consists of following structure:

![Purdue API Entities Hierarchy](https://camo.githubusercontent.com/cf0681aab8586f72f7dcdef36d4bd4fafe7769fd/687474703a2f2f692e696d6775722e636f6d2f4e7952654553432e706e67)
*Purdue API Entities Hierarchy (Purdue API)*

Each entity has its own properties, so that properties can be accessible by method chaining.
For instance:

```php
Purdue::course('cs 180')->creditHours; // 4.0
Purdue::course('phys 172')->countCourses(); // 2 'Regular' and 'Honors'

Purdue::summer(2016)->termBegin;
Purdue::summer(2016)->termEnd;
```

Additionally, the package also offers filtering methods such as:
```php
 // Returns sections that 'Type' is matched with $type. 'CS 180' has 'Lecture' and 'Laboratory'.
Purdue::course('cs 180')
       ->classes()
       ->sections()
       ->type('Lecture')
       ->getSections();
      
// Returns sections that have 'Remaining Space' greater than 20 and less then 60.
Purdue::course('cs 180')
        ->classes()
        ->sections()
        ->type('Laboratory')
        ->spaceGreaterThan(20)
        ->spaceLessThan(60)
        ->getSections();
```

For more details, please refer to this [wiki](https://github.com/dongyukang/purduecourse/wiki).

## Application

All set with the coding (although there's a lot more to fix and add), so did I accomplish the objective to this project? Here is another project I wrote with laravel php framework, named [**Purlanner**](https://github.com/dongyukang/purlanner). Shortly describing, the meaning of it is a combination of two words, Purdue + Planner. Basically, it is an agenda that helps users to organize school assignments, projects, tests and any other academic related tasks and enable them to plainly check all the due dates that is registered. 
Writing such application, I thought it would be better if users can access course info, instead of having them manually registering every course that they are taking. Additionally, I also thought of building a huge online communication system sharing students' thoughts based on their assignments that they registered to Purlanner, I thought being able to access Purdue's massive course info was necessary. So circling back to the first question, did I accomplish the objective to this project? Yes, definitely. It clearly helped me to code much efficient way. I was able to build this web app much faster than I thought through 'easy-to-read & write' method chaining. Repeating process of parsing data and requesting data was no longer an issue while developing this web app.         

## Summing up

So I wrote the package [```dongyukang/purduecourse```](https://github.com/dongyukang/purduecourse) 5 years ago. I also wrote the [**Purlanner**](https://github.com/dongyukang/purlanner) 5 years ago. Though I was not able to achieve my ultimate end-game goal of building a huge online community, I believe this is because not many people knew and used my application. Even if my product was well-advertised, I doubt that it would become popular among Purdue students. But I consider this as one of my trials, and I can take it as lesson to improve on. 



