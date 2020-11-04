# Enable-Access-Control-Allow-Origin-for-multiple-domains-in-Node.js
Enable Access-Control-Allow-Origin for multiple domains in Node.js

<h3>Here is what I use in my express application to allow multiple origins</h3>

<pre>
app.use((req, res, next) => {
  const allowedOrigins = ['http://127.0.0.1:8020', 'http://localhost:8020', 'http://127.0.0.1:9000', 'http://localhost:9000'];
  const origin = req.headers.origin;
  if (allowedOrigins.includes(origin)) {
       res.setHeader('Access-Control-Allow-Origin', origin);
  }
  //res.header('Access-Control-Allow-Origin', 'http://127.0.0.1:8020');
  res.header('Access-Control-Allow-Methods', 'GET, OPTIONS');
  res.header('Access-Control-Allow-Headers', 'Content-Type, Authorization');
  res.header('Access-Control-Allow-Credentials', true);
  return next();
});
</pre>
