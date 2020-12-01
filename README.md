# Pizza Hunt   

## Description:

![License](https://img.shields.io/badge/License-MIT-blue.svg "License Badge")

This is a full stack web application that uses the power of MongoDB to create a noSQL database that stores user inputted information from the front end pages. More specifically, this application is designed for building custom pizza recipies, and collaborating with a community of other pizza enthusiasts to create the ultimate pizza.


# Table of Contents 

- [Repository](#repository)
- [Examples](#examples)
- [Usage](#usage)
- [Contributions](#contributing)
- [Tests](#tests)
- [License](#license)
- [Questions](#questions)
- [Technologies Used](#languages)

## Repository: 
- [My Github Profile](https://github.com/suschuk24)

- [This Repository](https://github.com/suschuk24/new-social-network)

- [Deployed Application](https://pizza-hunt-112420.herokuapp.com/)


## Examples
Landing Page
![landing page screenshot](/public/assets/images/landing-page.jpg)

Make a custom pizza!
![custom pizza](/public/assets/images/create-pizza.jpg)

After creating a pizza, other users can comment on your masterpiece!
![pizza conversation](/public/assets/images/pizza-conversation.jpg)

* Incoming Pizza Object Sent via POST Request:
``` JSON
{
    "pizzaName": "Best pizza ever!",
    "createdBy": "Seth",
    "size": "Personal",
    "toppings": [
        "Sausage",
        "Pepperoni",
        "Cherry Peppers"
    ]
}
```
* Incoming Comment Object Sent via clickHandler() function via POST request:

``` JSON
{
  "writtenBy": "Amikoson",
  "commentBody": "I don't know, it's pretty good."
}
```
* Comment Reply Object: 
``` JSON
{
        "replyBody": "I agree, its delicious!"
      }
```

* Complete Pizza Object with Associated array of comment objects, associated comment reply objects, and the reply count. 
``` JSON
{
    "size": "Personal",
    "toppings": [
      "Sausage",
      "Pepperoni",
      "Cherry Peppers"
    ],
    "comments": [
      {
        "_id": "5fbd9cfa1c97fe417c491a67",
        "commentBody": "I don't know, it's pretty good.",
        "writtenBy": "Amikoson",
        "createdAt": "Nov 24th, 2020 at 17:53 pm",
        "replies": [
          {
            "_id": "5fbd9d011c97fe417c491a68",
            "writtenBy": "Seth",
            "replyBody": "I agree, its delicious!",
            "replyId": "5fbd9d011c97fe417c491a69",
            "createdAt": "Nov 24th, 2020 at 17:57 pm",
            "id": "5fbd9d011c97fe417c491a68"
          }
        ],
        "replyCount": 1
      }
    ],
    "_id": "5fbd5358409b793d14ab8630",
    "pizzaName": "Best pizza ever!",
    "createdBy": "Seth",
    "createdAt": "Nov 24th, 2020 at 12:39 pm",
    "commentCount": 2
  }
```

### Note
 Object may be trimmed down to present only relevent information. This can be easily changed in the controllers files, in each API function, you can choose which object elements to display or hide.
 
 Consider the following code from this application:
 ``` JavaScript
getAllPizza(req, res) {
        Pizza.find({})
            .populate({
                path: 'comments',
                select: '-__v'
            })
            .select('-__v')
            .sort({ _id: -1 })
            .then(dbPizzaData => res.json(dbPizzaData))
            .catch(err => {
                console.log(err)
                res.status(400).json(err)
            });
    },
 ```
  If a developer wants to hide the ```_id``` value in the Pizza Object, they would simply add another ```.select()``` function, passing the ```_id``` value through it, with the ```-``` prefix to indicate it to be excluded; wrapped inside quotations. Please see the following code block and notice the second ```.select()``` function,
  ``` JavaScript
 getAllPizza(req, res) {
        Pizza.find({})
            .populate({
                path: 'comments',
                select: '-__v'
            })
            .select('-__v')
            .select('-_id')
            .sort({ _id: -1 })
            .then(dbPizzaData => res.json(dbPizzaData))
            .catch(err => {
                console.log(err)
                res.status(400).json(err)
            });
    },
  ```
  
## Usage:

This is a full stack web application for building custom pizza recipies, and collaborating with a community of other pizza enthusiasts to create the ultimate pizza. 

## License:
For more information about licenses, please visit:
[License](https://opensource.org/licenses/MIT)

## Contributing:

[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg)](CODE_OF_CONDUCT.md)

Seth Uschuk


## Tests:

Testing completed using InsomniaCore, Checked for typos and bugs


## Technologies Used:

* JavaScript
* Node
* Express
* Mongoose
* CSS
* HTML
* Heroku


## Questions:


If you have any questions, please see my GitHub Page, or feel free to reach out by email:

-[GitHub's Guide to a Professional README](https://github.com/coding-boot-camp/potential-enigma/blob/master/readme-guide.md)


- [My Github Profile](https://github.com/suschuk24)

- [This Repository](https://github.com/suschuk24/pizza-hunt)

- [My Email](test@gmail.com)

  
