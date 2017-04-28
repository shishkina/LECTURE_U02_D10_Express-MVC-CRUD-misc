# Express MVC continued, the UD of CRUD

## Objectives

1. Explain method override
2. Describe and implement update functionality to adaquote
3. Describe and implement delete functionality to adaquote
4. Review Express MVC at a high level
5. practice, practice, practice...with deep breaths in between

## Method override and submitting `PUT`s and `DELETE`s

So far we've read all of the items in our database (`GET`) and we've added items to our database (`POST`). Now we're going to learn how to edit (`PUT`) and delete items in the database (`DELETE`).

Unfortunately, `PUT` and `DELETE` are not quite supported in the web browser. We have to install and use an express middleware called 'method override' to get them to work:

1. Run `npm install --save method-override`
2. Then you have to import it:
```javascript
const methodOverride = require('method-override');
```
3. Next, you'll use the middleware in the area of `app.js` where you use other middleware like `body-parser`:
```javascript
app.use(methodOverride('_method'));
```

4. Finally, you'll have to add the method override as a parameter to the URL in the form. Compare the following `POST` and `PUT` forms:

`POST`:
```javascript
<form method='POST' action='/quotes'>
  <input name='content' type='text' placeholder='Quote' />
  <input name='author' type='text' placeholder='Author' />
  <input name='genre_id' type='text' placeholder='Genre' />
  <input type='submit' value='Add it!' />
</form>
```

`PUT`:
```javascript
<form method='POST' action='/quotes/<%= id %>?_method=PUT'>
  <input name='content' type='text' value='<%= quote.content %>' />
  <input name='author' type='text' value='<%= quote.author %>' />
  <input name='genre_id' type='text' value='<%= quote.genre_id %>' />
  <input type='submit' value='Edit it!' />
</form>
```

## Adding some routes, models, views, and controllers

1. We've added some new routes for accessing the edit form, submitting an update, and for deleting: see `routes/quotes.js`, lines 12, 15, and 16.

2. We've added a view for the edit form: see `views/quotes/quotes-edit.ejs`.

3. There are some new controllers to handle these routes: see `controllers/quotes/quotesController.js`, lines 45-82.

4. Finally, we have some new models that interact directly with our PostgreSQL database: see `models/quote.js`, lines 24-45.

## Fixing some bugs

1. See line 6 in `models/quote.js`. **Question: why did we have to do that?**
2. See line 6 in `views/quotes/quotes-index.ejs`. **Question: what did we change? Why do you think we had to do that?**

## Lab!

1. Continue yesterday's lab. If you finished yesterday's portion, minus the styling, continue on to today's topics and try to add edit and delete functionality to the movies app.

**BONUS**

2. If you produce a fully CRUD movies app, take a shot at including a javascript file that will run in the browser. What steps would that require? Hint: you should put a `.js` file somewhere in the public folder and then link it to your website somehow...maybe in the `index.ejs`, or `boilerplate.ejs`, or `end.ejs`?
3. Try just getting a `console.log()` in the browser. After you do that try to do some DOM manipulation and then see if you can do some fetching.
4. We'll talk about these topics in the afternoon!

