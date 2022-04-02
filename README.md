# baycity-news
## creating the home page
The express.static() method is a built-in Express.js middleware function that can take all of the contents of a folder and serve them as static assets. This is useful for front-end specific files like images, style sheets, and JavaScript files.

In previous full-stack projects you've created, the app served static HTML and JavaScript files. In those cases, to display the actual data from the database, the JavaScript code on the front end had to make a follow-up request to an endpoint like /api/animals using the Fetch API. This approach works, but there is a brief second where the user sees an empty layout while the network request goes through.

Even if that moment of loading is acceptable to your users, the extra network requests can still be a burden on your server. Plus, your app won't perform as well in search engines, because the data you want them to see and index isn't available on the initial request. And search engine visibility is the whole point of Bay city News!

One way around this would be to send back the data and HTML in the same string.

Unfortunately, writing HTML content as a string isn't very intuitive or maintainable. That's when a template engine comes in handy. Template engines allow you to write HTML code in a more familiar environment, leaving placeholders like `{{ some_data }}` for the data you want to be merged in. For Bay city News, we'll use the Handlebars.js template engine.

To get started with Handlebars.js, you first need to install the correct dependency by typing the following command:

`npm install express-handlebars`

IMPORTANT
Your file/folder structure MUST be set up this way for Handlebars.js to work correctly. You will always have a main layout located at (and named) views/layouts/main.handlebars. All other template files will go directly in the views folder (i.e. views/welcome.handlebars).

## Introducing the Model-View-Controller Paradigm
Why does Handlebars.js require a views folder? Why can't this be named something else? The reason for this is that Handlebars.js is meant to fit into an existing architectural paradigm called Model-View-Controller, or MVC.

Let's rename the routes folder to controllers so the MVC structure is more obvious.

Because you renamed the folder, you'll need to update the reference in server.js to what's shown in the following code:

`const routes = require('./controllers/');`

MVC is a popular software-design pattern that organizes your app into the three following separate concerns:

Models: the core data of your app

Views: the UI components, such as your HTML layouts

Controllers: the link between your models and views

## Let's add some data to the homepage. The res.render() method can accept a second argument, an object, which includes all of the data you want to pass to your template. In home-routes.js, update the homepage route to look like the following code:
```js
router.get('/', (req, res) => {
  res.render('homepage', {
    id: 1,
    post_url: 'https://handlebarsjs.com/guide/',
    title: 'Handlebars Docs',
    created_at: new Date(),
    vote_count: 10,
    comments: [{}, {}],
    user: {
      username: 'test_user'
    }
  });
});
```

## bcrypt concepts
Why is async mode recommended over sync mode?

If you are using bcrypt on a simple script, using the sync mode is perfectly fine. However, if you are using bcrypt on a server, the async mode is recommended. This is because the hashing done by bcrypt is CPU intensive, so the sync version will block the event loop and prevent your application from servicing any other inbound requests or events. The async version uses a thread pool which does not block the main event loop.
So, for a better user experience on a live app, choose the async version to reduce the time a user has to wait to verify the password.

##