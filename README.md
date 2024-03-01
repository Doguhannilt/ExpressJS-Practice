<h1>Express JS Tutorial by <a hreF="https://www.youtube.com/playlist?list=PL0Zuz27SZ-6P4vnjQ_PJ5iRYsqJkQhtUu">Dave Gray</a></h1>

<p>Hi, this repository is heavily influenced by <i>Dave Gray</i>'s ExpressJS tutorial on his YouTube channel. I will share every file, note, and tips that I got from the tutorial and some several sources. </p>

### DAY 1

#### Note 1:
<table>
  <tr>
    <td>You need to know what NodeJS is and how to use it to make the most out of Express.</td>
  </tr>
</table>

#### Note 2:
<table>
  <tr>
    <td>Commands</td>
    <td></td>
  </tr>
  <tr>
    <td><code>npm update</code></td>
    <td>Updates dependencies</td>
  </tr>
  <tr>
    <td><code>npm install</code></td>
    <td>Installs dependencies</td>
  </tr>
</table>

#### Note 3:
<table>
  <tr>
    <td>Traditional Express Method</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <pre><code>app.get('/', (req, res) => {
    res.send("Hello World");
});</code></pre>
    </td>
    <td>
      <ul>
        <li><code>app</code>: Variable derived from <code>const app = express()</code></li>
        <li><code>get()</code>: Represents a <strong>GET Request</strong></li>
        <li><code>'/'</code>: The specific URL used in the process</li>
        <li><code>(req, res)</code>: A messaging pattern allowing two applications to converse over a channel</li>
      </ul>
    </td>
  </tr>
</table>

#### Note 4:
<table>
  <tr>
    <td>Using <code>res.sendFile()</code></td>
    <td></td>
  </tr>
  <tr>
    <td>- This function transfers a file at the given path.</td>
    <td></td>
  </tr>
  <tr>
    <td>- Syntax: <code>res.sendFile(path [, options] [, fn])</code></td>
    <td></td>
  </tr>
  <tr>
    <td>Example:</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <pre><code>app.get('/', (req, res) => {
    res.sendFile('./views/index.html', { root: __dirname });
});</code></pre>
    </td>
    <td> 
    <pre><code>app.get('/', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'index.html'))
});</code></pre></td>
  </tr>
</table>

#### Note 5:
<table>
  <tr>
    <td>What if we want to specify two direction for only one page?</td>
    <td></td>
  </tr>
  <tr>
    
<tr>
    <td>
      <pre><code>app.get('^/$|/index.html', (req, res) => {
    res.sendFile('./views/index.html', { root: __dirname });
});</code></pre>
    </td>
  </tr>
</table>

#### Note 6:
<table>
  <tr>
    <td>What if we want to make '.html' extension is only optional?</td>
    <td></td>
  </tr>
    <tr>
    <td>
      <pre><code>app.get('^/$|/index(.html)?', (req,res) => {
    res.sendFile(path.join(__dirname, 'views', 'index.html'))
})</code></pre>
    </td>
  </tr>
</table>

#### Note 7:
<table>
  <tr>
    <td>What if our web page is permanently moved to another webpage? (REDIRECTING)</td>
    <td></td>
  </tr>
    <tr>
    <td>
      <pre><code>app.get('/old-page.html', (req,res) => {
    res.redirect(301, '/new-page.html')
})</code></pre>
    </td>
  </tr>
</table>

#### Additional (<a href ="https://expressjs.com/en/guide/routing.html">Route Parameters</a>)

<table>
  <tr>
    <td><strong>Description</strong></td>
    <td><strong>Example</strong></td>
    <td><strong>Request URL</strong></td>
    <td><strong>req.params</strong></td>
  </tr>
  <tr>
    <td>Named URL segments used to capture values in the URL.</td>
    <td><code>/users/:userId/books/:bookId</code></td>
    <td><code>http://localhost:3000/users/34/books/8989</code></td>
    <td><code>{ "userId": "34", "bookId": "8989" }</code></td>
  </tr>
  <tr>
    <td>Route path parameters defined with word characters ([A-Za-z0-9_]).</td>
    <td><code>/users/:userId/books/:bookId</code></td>
    <td><code>http://localhost:3000/users/34/books/8989</code></td>
    <td><code>{ "userId": "34", "bookId": "8989" }</code></td>
  </tr>
  <tr>
    <td>Using hyphen (-) and dot (.) literals in route parameters.</td>
    <td><code>/flights/:from-:to</code></td>
    <td><code>http://localhost:3000/flights/LAX-SFO</code></td>
    <td><code>{ "from": "LAX", "to": "SFO" }</code></td>
  </tr>
  <tr>
    <td>Utilizing dot (.) in route parameters for specific purposes.</td>
    <td><code>/plantae/:genus.:species</code></td>
    <td><code>http://localhost:3000/plantae/Prunus.persica</code></td>
    <td><code>{ "genus": "Prunus", "species": "persica" }</code></td>
  </tr>
  <tr>
    <td>Applying regular expressions for precise matching of route parameters.</td>
    <td><code>/user/:userId(\d+)</code></td>
    <td><code>http://localhost:3000/user/42</code></td>
    <td><code>{ "userId": "42" }</code></td>
  </tr>
</table>




