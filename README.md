# baycity-news
## creating the home page
The express.static() method is a built-in Express.js middleware function that can take all of the contents of a folder and serve them as static assets. This is useful for front-end specific files like images, style sheets, and JavaScript files.

In previous full-stack projects you've created, the app served static HTML and JavaScript files. In those cases, to display the actual data from the database, the JavaScript code on the front end had to make a follow-up request to an endpoint like /api/animals using the Fetch API. This approach works, but there is a brief second where the user sees an empty layout while the network request goes through.

Even if that moment of loading is acceptable to your users, the extra network requests can still be a burden on your server. Plus, your app won't perform as well in search engines, because the data you want them to see and index isn't available on the initial request. And search engine visibility is the whole point of Bay city News!

One way around this would be to send back the data and HTML in the same string.

Unfortunately, writing HTML content as a string isn't very intuitive or maintainable. That's when a template engine comes in handy. Template engines allow you to write HTML code in a more familiar environment, leaving placeholders like `{{ some_data }}` for the data you want to be merged in. For Bay city News, we'll use the Handlebars.js template engine.

To get started with Handlebars.js, you first need to install the correct dependency by typing the following command:

`npm install express-handlebars`