# Silvia's Notes
## Summary
This repository contains all of the notes taken by [Silvia](https://github.com/silvhua) for [Lighthouse Labs](https://www.lighthouselabs.ca/) Data Science Bootcamp.

## Table of Contents
* Python Course
    * [Unit 1](/unit01/)
        * [Day 1](/unit01/day01/)
        * [2022-09-20](#2022-09-20-intro-to-python)
        * [2022-09-21 APIs](#2022-09-21-apis)

### Tips

Try experimenting with the comparison operators (`<`, `>`, `===`, etc.) in the node REPL, which you can launch using the `node` command in Vagrant.

Work on your code iteratively – that means in small pieces. 

To help you figure out how to use `hungry` and `availableTime` inside your function, try outputting their values to the Terminal as follows.

```javascript
function whatToDoForLunch(hungry, availableTime) {
  console.log("hungry is", hungry);
  console.log("availableTime is", availableTime);
}
```
## 2022-09-20 Intro to Python
Instructor: Simon Dawkins, lead instructor. 

#### Numbers
* Ways to round numbers:
    * `c = round(number,decimalplaces)`
    * Casting between integers and floats
        * `c = float(a)`
        * `d = int(b)`  rounds it down

#### Lists
* To append items to a list, use one of 2 options:
    * list.append(x)
    * list = list + [x]
* Splitting strings into lists: 
    `b = a.split()` where default delimiter is space, but can be specified in the parentheses

#### Tuples
* Advantage over lists:
    * Unpacking: `name, language, country = x`
        * Unpacking can be done with lists, but this is less safe because lists can change, whereas tuples cannot.
    * Checking membership is faster: `y = 12 in x`
* Best practices:
    * Lists used when all data are of the same type
    * Tuples used when data are of different types

#### Dictionaries
* Important methods:
    * `x.keys()`
    * `x.values()`
    * `x.items()`
        * e.g. of unpacking in a for loop: 
        
                for key, value in x.items()

#### Sets
* Data structure that:
    * Are unordered, meaning there is no element 0 and element 1
    * the values contained are unique; no duplicate values
    * Are made with curly brackets

```python
myset = {2, 1.0, 'apple', 1.0, 'apPle'}
```

* Data sets are not commonly used. They can be useful due to the fact that all values are unique.

#### Booleans and Logical Operators
```
sunny = True
```
`if sunny == True:` is the same as `if sunny:` because before, we defined `sunny = True`

#### Control Flow: For Loops (Definite Iterations)
```
for [variable] in [iterable data structure like a list]:
    [what you want to do using the current value in each iteration]
```
* Best practice is to make the variable descriptive to improve readability of the code
* An **accumulator variable** increases with iterations. It usually gets defined at zero before the for loop.

#### Control Flow: While Loops (Indefinite Iterations)
* Use CTRL + C to quit any code run, e.g. if running an infinite loop.

#### Defining Functions
* Arguments get passed into a parameter
* Default parameter value can be specified in the function in case no arguments are provided for that parameter.

```Python
def whatismyname(name='Name')
    print("Your name is " + str(name))

whatismyname()
# output will be Your name is Name because no argument was entered.
```
[Table of Contents](#table-of-contents)

## 2022-09-21 APIs
Instructor: Samual Boylan (in Toronto)
Interest in neural networks & deep learning, cryptocurrency API, robotics

* You can upload Jupyter notebook to Google Collab to see if the issue is due to the actual code or due to your computer.
* Kaggle.com is a place to get public datasets.

### Accessing APIs
* **endpoints**: Routes to get data. There may be multiple.
* **parameters**: What you pass into the API to get desired info.
* **response fields**: Data you get out of the API.
* API requests are made by *HTTP requests*
    * 80% are GET requests to retrieve data (using parameters)
    * POST requests are for sending information to a server
* Status codes:
    * 200: OK; this is what we want
    * 400: bad request
    * 401: unauthorized
    * 404: not found
    * 500s: server has the issue

#### Command Line API calls
* In real applications, API calls won't be done using command line (`curl` command), but the documentation for curl API calls will give the URL
```
curl <URL>?apikey=<api key>
```
To create environment variables in Windows (e.g. to hide API key), search "environment variables" in start menu.

#### Postman API calls
* Postman API calls aren't really used for real applications, but used to make sure the API calls work before trying it in code.
* To get response in JSON format, under "Headers", specify that (requires manual entry of specific text; see API documentation)

#### Python API calls
```Python
import requests
import os
```
* *For now, don't worry too much about creating environment variables if having technical issues, since we won't be transmitting sensitive info.*
* **In URL of API call, separate multiple parameters using `&` symbol**
* Data in JSON format is a dictionary so has same methods/functions in Python.
* Parameters can be put into a dictionary that can be passed into the API request URL. 

## Stuff I did after class
```Ubuntu command line
export FOURSQUARE_API_KEY=fsq3y7QH0WSEhjn4m+9v+uHu8+3YgmQWnKmQ6Mcw60ZSdT0=
```

[Table of Contents](#table-of-contents)

# 2022-09-22 Projects in Data Science
Simon Dawkins
* Exclamation mark at start of line in notebook allows for you to run command line prompts.
* Need to install additional modules/package to the same python package to make them run.
* No need to use windows command line, powershell, Anaconda prompt, or git bash ever on Windows because can use Ubuntu.

## Projects in Data Science
* Benchmarking a new technique
* New use-case for existing technique

## Collaboration
* In pairs, better to work on different subtasks than to work on the same task
* Code reviews are a good idea to have another pair of eyes to review and to see another way of doing things
* Only push to GitHub when code works so no one pulls bad code

## This week's mini project
* Part 1: Practice working with:
    * Using poor documentation
    * Parsing complex data structrures
* Mini projects #2 and 4 will be evaluated.
## Code
* Define functions whenever something needs to be done more than once.
* Save results of GET requests to a file and only fetch when needed
    * Avoid being misidentified as a bot
* Jupyter cells should have a clearly defined goal so you only run what you need each time

## Explore the Dataset, API, and other Tools
* Look at the variables and data
* Plot the data: matplotlib, seaborn

## Presentation
* Present as if for a client who doesn't have technical knowledge
    * Avoid showing code unless there's something remarkable/unusual
* Make it a story
    * What is the problem? Why is it important?

### Structure
* Motivation: problem, importance
* Task
    * Problem from a technical perspective
    * Description of dataset
* Modeling
    * Use schematics
* Results
* Conclusions

[draw.io](draw.io) is a good resource for creating figures
