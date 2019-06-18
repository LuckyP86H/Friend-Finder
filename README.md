# Friend Finder - Node and Express Servers

## Overview

This app is aiming to build a compatibility-based "FriendFinder" application -- basically a dating app. This full-stack site will take in results from your users' surveys, then compare their answers with those from other users. It will then display the name and picture of the user with the best overall match.

## Preparation

* Check out [this demo version of the site](https://friend-finder-fsf.herokuapp.com/). Use this as a model for how we expect your assignment look and operate.

* Create a folder called `FriendFinder`. Inside the folder, organize your directories so it matches the following:

```
FriendFinder
- .gitignore
- app
- data
- friends.js
- public
- home.html
- survey.html
- routing
- apiRoutes.js
- htmlRoutes.js
- node_modules
- package.json
- server.js
```

## Instructions

1. The servey have 10 questions of your choosing. Each answer should be on a scale of 1 to 5 based on how much the user agrees or disagrees with a question.

2. The file, `server.js`, should require the basic npm packages used in class: `express` and `path`.

3. The file, `htmlRoutes.js`, should include two routes:

    * A GET Route to `/survey` which should display the survey page.
    * A default, catch-all route that leads to `home.html` which displays the home page.

4. The file, `apiRoutes.js`, should contain two routes:

    * A GET route with the url `/api/friends`. This will be used to display a JSON of all possible friends.
    * A POST routes `/api/friends`. This will be used to handle incoming survey results. This route will also be used to handle the compatibility logic.

5. The application data is saved inside of `app/data/friends.js` as an array of objects. Each of these objects should roughly follow the format below.

```json
{
"name":"Ahmed",
"photo":"https://media.licdn.com/mpr/mpr/shrinknp_400_400/p/6/005/064/1bd/3435aa3.jpg",
"scores":[
5,
1,
4,
4,
5,
1,
2,
5,
4,
1
]
}
```

6. Determine the user's most compatible friend using the following as a guide:

    * Convert each user's results into a simple array of numbers (ex: `[5, 1, 4, 4, 5, 1, 2, 5, 4, 1]`).
    * With that done, compare the difference between current user's scores against those from other users, question by question. Add up the differences to calculate the `totalDifference`.
    * Example:
            - User 1: `[5, 1, 4, 4, 5, 1, 2, 5, 4, 1]`
            - User 2: `[3, 2, 6, 4, 5, 1, 2, 5, 4, 1]`
            - Total Difference: **2 + 1 + 2 =** **_5_**
    * . **Remember** to use the absolute value of the differences. Put another way: no negative solutions! 
        - The app should calculate both `5-3` and `3-5` as `2`, and so on.
        - The closest match will be the user with the least amount of difference.

7. Once the current user's most compatible friend is found, display the result as a modal pop-up.
   
   * The modal should display both the name and picture of the closest match.

- - -

### Hosting on Heroku

Now that the backend of my applications is hosting though heroku. Please note that while **Heroku is free**, it will request credit card information if you have more than 5 applications at a time or are adding a database.

- Please see [Heroku’s Account Verification Information](https://devcenter.heroku.com/articles/account-verification) for more details.
- See the [Supplemental Heroku Deployment Guide](../../03-Supplemental/HerokuGuide.md) for in-detail deployment instructions.

- - - 
&copy; Paul Xu June 2019
