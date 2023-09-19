You’ll build this site completely from scratch and deploy it to Heroku. Your app will follow the MVC paradigm in its architectural structure, using Handlebars.js as the templating language, Sequelize as the ORM, and the express-session npm package for authentication.

I am presented with the homepage, 
    which includes existing blog posts if any have been posted; 
    navigation links for the homepage and the dashboard; 
    and the option to log in
I click on the homepage option
    I am taken to the homepage
WHEN I click on any other links in the navigation
    THEN I am prompted to either sign up or sign in
WHEN I choose to sign up
    THEN I am prompted to create a username and password
WHEN I click on the sign-up button
    THEN my user credentials are saved and I am logged into the site
WHEN I revisit the site at a later time and choose to sign in
    THEN I am prompted to enter my username and password
WHEN I am signed in to the site
    THEN I see navigation links for 
        the homepage, 
        the dashboard, 
        and the option to log out
WHEN I click on the homepage option in the navigation
THEN I am taken to the homepage and presented with existing blog posts that include the post title and the date created
WHEN I click on an existing blog post
THEN I am presented with the post title, contents, post creator’s username, and date created for that post and have the option to leave a comment
WHEN I enter a comment and click on the submit button while signed in
THEN the comment is saved and the post is updated to display the comment, the comment creator’s username, and the date created
WHEN I click on the dashboard option in the navigation
THEN I am taken to the dashboard and presented with any blog posts I have already created and the option to add a new blog post
WHEN I click on the button to add a new blog post
THEN I am prompted to enter both a title and contents for my blog post
WHEN I click on the button to create a new blog post
THEN the title and contents of my post are saved and I am taken back to an updated dashboard with my new blog post
WHEN I click on one of my existing posts in the dashboard
THEN I am able to delete or update my post and taken back to an updated dashboard
WHEN I click on the logout option in the navigation
THEN I am signed out of the site
WHEN I am idle on the site for more than a set time
THEN I am able to view posts and comments but I am prompted to log in again before I can add, update, or delete posts
```

You'll just want to use document.location.replace('/dashboard') in the file in public/js/*.js that's handling the post - I see you have that in the profile, but after the delete or new project handler it's going to /profile instead of /dashboard(or the url for whatever page you mean by dashboard)

Some more specific steps will be:
-Create a Comment.js file in models
-Import sequelize, Model, etc
-Create a Comment.init() function that has whatever data you want to store with your comments, id, etc
-export the model
-in models/index.js you'll do the association itself: import your Comment model, using hasMany, associate the comment with the post table, set the foreignKey to the id, and other options
Then you can use the model in your controllers to actually add data and such.
Can I clarify anything else on this before I leave you to work on it?