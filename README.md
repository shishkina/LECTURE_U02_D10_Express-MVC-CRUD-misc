# Express MVC continued, the UD of CRUD

So far we've read all of the items in our database (`GET`) and we've added items to our database (`POST`). Now we're going to learn how to edit (`PUT`) and delete items in the database (`DELETE`).

Unfortunately, `PUT` and `DELETE` is not quite supported in the web browser. We have to install and use an express middleware called 'method override' to get them to work:

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
