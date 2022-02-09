# Natours Application


# Node JS

`npm -i express`

`npm -i morgan`

`npm -i mongoose`

<I have used the MongoDB Atlas>

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%201.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%202.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%203.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%204.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%205.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%206.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%207.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%208.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%209.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2010.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2011.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2012.png)

---

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2013.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2014.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2015.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2016.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2017.png)

```jsx
const http = require('http');

const server = http.createServer((req, res) => {
    console.log(res);
    res.end('Hello from the server');
});

server.listen(8000, '127.0.0.1', () => {
    console.log('Listening to requests on the port 8000');
})
```

```jsx
const fs = require("fs");
const crypto = require("crypto");

const start = Date.now();
process.env.UV_THREADPOOL_SIZE = 4;

setTimeout(() => console.log("Timer 1 finished"), 0);
setImmediate(() => console.log("Immediate 1 finished"));

fs.readFile("test-file.txt", () => {
  console.log("I/O finished");
  console.log("----------------");

  setTimeout(() => console.log("Timer 2 finished"), 0);
  setTimeout(() => console.log("Timer 3 finished"), 3000);
  setImmediate(() => console.log("Immediate 2 finished"));

  process.nextTick(() => console.log("Process.nextTick"));

  crypto.pbkdf2Sync("password", "salt", 100000, 1024, "sha512");
  console.log(Date.now() - start, "Password encrypted");

  crypto.pbkdf2Sync("password", "salt", 100000, 1024, "sha512");
  console.log(Date.now() - start, "Password encrypted");

  crypto.pbkdf2Sync("password", "salt", 100000, 1024, "sha512");
  console.log(Date.now() - start, "Password encrypted");

  crypto.pbkdf2Sync("password", "salt", 100000, 1024, "sha512");
  console.log(Date.now() - start, "Password encrypted");
});

console.log("Hello from the top-level code");
```

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2018.png)

```jsx
const EventEmitter = require("events");
const http = require("http");

// const myEmmitter = new EventEmitter();

class Sales extends EventEmitter {
  constructor() {
    super();
  }
}

const myEmitter = new Sales();

myEmitter.on("newSale", () => {     // Observer for the event
  console.log("There was a new sale!");
});

myEmitter.on("newSale", () => {
  console.log("Costumer name: Sanket");
});

myEmitter.on("newSale", stock => {
  console.log(`There are now ${stock} items left in stock.`);
});

myEmitter.emit('newSale');   // There was a new sale! 
                             // Costumer name: Sanket
myEmitter.emit("newSale", 9);   // Emits the event   //There are now 9 items left in stock.

//////////////////

const server = http.createServer();

server.on("request", (req, res) => {
  console.log("Request received!");
  console.log(req.url);
  res.end("Request received");
});

server.on("request", (req, res) => {
  console.log("Another request 😀");
});

server.on("close", () => {
  console.log("Server closed");
});

server.listen(8000, "127.0.0.1", () => {
  console.log("Waiting for requests...");
});
```

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2019.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2020.png)

```jsx
const fs = require("fs");
const server = require("http").createServer();

server.on("request", (req, res) => {
  // Solution 1
  // fs.readFile("test-file.txt", (err, data) => {
  //   if (err) console.log(err);
  //   res.end(data);
  // });

  // Solution 2: Streams
  // const readable = fs.createReadStream("test-file.txt");
  // readable.on("data", chunk => {
  //   res.write(chunk);
  // });
  // readable.on("end", () => {
  //   res.end();
  // });
  // readable.on("error", err => {
  //   console.log(err);
  //   res.statusCode = 500;
  //   res.end("File not found!");
  // });

  // Solution 3
  const readable = fs.createReadStream("test-file.txt");
  readable.pipe(res);
  // readableSource.pipe(writeableDest)
});

server.listen(8000, "127.0.0.1", () => {
  console.log("Listening...");
});
```

---

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2021.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2022.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2023.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2024.png)

```jsx
// console.log(arguments);
// console.log(require("module").wrapper);

// module.exports
const C = require("./test-module-1");
const calc1 = new C();
console.log(calc1.add(2, 5));

// exports
// const calc2 = require("./test-module-2");
const { add, multiply } = require("./test-module-2");
console.log(multiply(2, 5));

// caching
require("./test-module-3")();
require("./test-module-3")();
require("./test-module-3")();
```

test-module-1

```jsx
// class Calculator {
//   add(a, b) {
//     return a + b;
//   }

//   multiply(a, b) {
//     return a * b;
//   }

//   divide(a, b) {
//     return a / b;
//   }
// }

module.exports = class {
  add(a, b) {
    return a + b;
  }

  multiply(a, b) {
    return a * b;
  }

  divide(a, b) {
    return a / b;
  }
};
```

test-module-2

```jsx
exports.add = (a, b) => a + b;
exports.multiply = (a, b) => a * b;
exports.divide = (a, b) => a / b;
```

test-module-3

```jsx
console.log("Hello from the module");

module.exports = () => console.log("Log this beautiful text 😍");
```

**Asynchronous**

```jsx
const fs = require('fs');
const superagent = require('superagent');

const readFilePro = file => {
  return new Promise((resolve, reject) => {
    fs.readFile(file, (err, data) => {
      if (err) reject('I could not find that file 😢');
      resolve(data);
    });
  });
};

const writeFilePro = (file, data) => {
  return new Promise((resolve, reject) => {
    fs.writeFile(file, data, err => {
      if (err) reject('Could not write file 😢');
      resolve('success');
    });
  });
};

const getDogPic = async () => {
  try {
    const data = await readFilePro(`${__dirname}/dog.txt`);
    console.log(`Breed: ${data}`);

    const res1Pro = superagent.get(
      `https://dog.ceo/api/breed/${data}/images/random`
    );
    const res2Pro = superagent.get(
      `https://dog.ceo/api/breed/${data}/images/random`
    );
    const res3Pro = superagent.get(
      `https://dog.ceo/api/breed/${data}/images/random`
    );
    const all = await Promise.all([res1Pro, res2Pro, res3Pro]);
    const imgs = all.map(el => el.body.message);
    console.log(imgs);

    await writeFilePro('dog-img.txt', imgs.join('\n'));
    console.log('Random dog image saved to file!');
  } catch (err) {
    console.log(err);

    throw err;
  }
  return '2: READY 🐶';
};

(async () => {
  try {
    console.log('1: Will get dog pics!');
    const x = await getDogPic();
    console.log(x);
    console.log('3: Done getting dog pics!');
  } catch (err) {
    console.log('ERROR 💥');
  }
})();

/*
console.log('1: Will get dog pics!');
getDogPic()
  .then(x => {
    console.log(x);
    console.log('3: Done getting dog pics!');
  })
  .catch(err => {
    console.log('ERROR 💥');
  });
*/
/*
readFilePro(`${__dirname}/dog.txt`)
  .then(data => {
    console.log(`Breed: ${data}`);
    return superagent.get(`https://dog.ceo/api/breed/${data}/images/random`);
  })
  .then(res => {
    console.log(res.body.message);
    return writeFilePro('dog-img.txt', res.body.message);
  })
  .then(() => {
    console.log('Random dog image saved to file!');
  })
  .catch(err => {
    console.log(err);
  });
*/
```

---

---

---

---

---

---

---

---

---

---

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2025.png)

`npm init`

Project Name: `Natours`

`npm i express@4`

```jsx
const express = require('express');
const app=express();

app.get('/',(res,req)=>{    // if we hit '/' route then the call back will send the below content as a response
// with the status code as 200(Ok).
	res.status(200).send('Hello from the server side');
});

app.post('/',(res,req)=>{
		res.send('you can post  to this endpoint...');
});

const port = 3000;
app.listen(port,()=>{
console.log(`App running on port ${port}...`);
});

```

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2026.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2027.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2028.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2029.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2030.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2031.png)

---

---

---

```jsx

const fs = require('fs');
const express = require('express');

const app=express();
app.use(express.json());  // middleware 

const tours = JSON.parse(
	fs.readFileSync(`${__dirname}/dev-data/data/tours-simple.json`)
);

// get-- get all tours 
app.get('/api/v1/tours',(req,res)=>{
	res.status(200).json({
		status: 'success',
		results: tours.length,
		data:{
			tours
	}
});
});

// get-- get tours for the specified id 
app.get('/api/v1/tours/:id',(req,res)=>{
	//console.log(req.params);
	const id = req.params.id*1;   // convert the sting to number
	const tour = tours.find(el => el.id === id)   

if(!tour){
	return res.status(404).json({
		status: 'fail',
		message: 'Invalid Id'
	});
}

	res.status(200).json({
		status: 'success',
		data:{
		tour
		}
});
});

// post -- create a new tour 
	app.post('/api/v1/tours',(req,res)=>{
	//	console.log(req.body);
	const newID = tours[tours.length-1].id+1;
	const newTours = Object.assign({id:newId},req.body);
	tours.push(newTours);
	fs.writeFile(`${__dirname}/dev-data/data/tours-simple.json`,JSON.stringify(tours),err=>{
		res.status(201).json({
		status: 'success',
		data: {
			tour: newTour
	}
});
});

// patch-- to update the tour data for the given id
app.patch('/api/v1/tours/:id',(req,res)=>{
	
res.status(200).json({
	status: 'success',
data:{
	tour: '<updated tour here...>'
}
});
});

// delete the tour with the given id
app.delete('/api/v1/tours/:id',(req,res)=>{
res.status(204).json({
	status: 'success',
data: null
});
});

	res.send('Done');
})
```

---

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2032.png)

---

`npm i dotenv` 

console.log(process.env)

`npm i eslint prettier eslint-config-prettier eslint-plugin-prettier eslint-config-airbnb eslint-plugin-node eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react --save-dev`

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2033.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2034.png)

```
> use natours-test   <- create a DB
> use 
> db.tours.insertMany()
> db.tours.insertOne()
> db.find()         > db.find({})
> show dbs 
> show collections
$lte <- less than equals
$lt <- less than 
$gte 
$gt 

db.tours.find({ $or: [ {price: {$lt: 5000}} , {rating: {$gte: 4.8}} ]})   

> db.tours.updateOne({name: "The snow Adventurer"}, {$set: {price: 597}})
> db.tours.updateMany({},{$set:{}});

> db.tours.deleteMany({})
```

---

`npm i mongoose@5`

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2035.png)

 

```
// Creating the Schema

const tourSchema = **new mongoose.Schema({**
// adding the required schema here, also we can add the validator
});

// creating the model
const Tour  = mongoose.model('Tour',tourSchema); 

// Creating the document 

const testTour = new Tour({
	name: '',
	rating: ,
	price: 
});

// save the document to the database, it will return the promise that we have to consume
testTour.save().then(doc=> {
	console.log(doc);
}).catch(err=>{
	console.log(err);
});

```

---

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2036.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2037.png)

[Mongoose v6.0.12: Queries (mongoosejs.com)](https://mongoosejs.com/docs/queries.html)

- `[Model.deleteMany()](https://mongoosejs.com/docs/api.html#model_Model.deleteMany)`
- `[Model.deleteOne()](https://mongoosejs.com/docs/api.html#model_Model.deleteOne)`
- `[Model.find()](https://mongoosejs.com/docs/api.html#model_Model.find)`
- `[Model.findById()](https://mongoosejs.com/docs/api.html#model_Model.findById)`
- `[Model.findByIdAndDelete()](https://mongoosejs.com/docs/api.html#model_Model.findByIdAndDelete)`
- `[Model.findByIdAndRemove()](https://mongoosejs.com/docs/api.html#model_Model.findByIdAndRemove)`
- `[Model.findByIdAndUpdate()](https://mongoosejs.com/docs/api.html#model_Model.findByIdAndUpdate)`
- `[Model.findOne()](https://mongoosejs.com/docs/api.html#model_Model.findOne)`
- `[Model.findOneAndDelete()](https://mongoosejs.com/docs/api.html#model_Model.findOneAndDelete)`
- `[Model.findOneAndRemove()](https://mongoosejs.com/docs/api.html#model_Model.findOneAndRemove)`
- `[Model.findOneAndReplace()](https://mongoosejs.com/docs/api.html#model_Model.findOneAndReplace)`
- `[Model.findOneAndUpdate()](https://mongoosejs.com/docs/api.html#model_Model.findOneAndUpdate)`
- `[Model.replaceOne()](https://mongoosejs.com/docs/api.html#model_Model.replaceOne)`
- `[Model.updateMany()](https://mongoosejs.com/docs/api.html#model_Model.updateMany)`
- `[Model.updateOne()](https://mongoosejs.com/docs/api.html#model_Model.updateOne)`

---

### Debugging Node.js with ndb

`npm i ndb --global`

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2038.png)

---

for password hashing

`npm i bcryptjs`

```jsx
const bcrypt = require('bcryptjs');

const passwordHash = await bcrypt.hash('Pa$$w0rd', 10);

```

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2039.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2040.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2041.png)

`npm i jsonwebtoken`

---

Assigned a role for an application.

```jsx
role: {
    type: String,
    enum: ['user', 'guide', 'lead-guide', 'admin'],
    default: 'user'
  }
```

Grant access for a specific role, to perform the action. 

```jsx
exports.restrictTo = (...roles) => {
  return (req, res, next) => {
    // roles ['admin', 'lead-guide']. role='user'
    if (!roles.includes(req.user.role)) {
      return next(
        new AppError('You do not have permission to perform this action', 403)
      );
    }

    next();
  };
};
```

Here, I have used the restrict the deletion of any tour to only 'admin' and 'lead-guide', 

I have checked that thus the current role using the middleware. If the role is true then only the next() middleware will execute.

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2042.png)

---

Password reset & forgot password 

```jsx
userSchema.methods.createPasswordResetToken = function() {
  const resetToken = crypto.randomBytes(32).toString('hex');

  this.passwordResetToken = crypto
    .createHash('sha256')
    .update(resetToken)
    .digest('hex');

  console.log({ resetToken }, this.passwordResetToken);

  this.passwordResetExpires = Date.now() + 10 * 60 * 1000;

  return resetToken;
};
```

---

Sending the email through the nodemailer

```jsx
const nodemailer = require('nodemailer');

const sendEmail = async options => {
  // 1) Create a transporter
  const transporter = nodemailer.createTransport({
    host: process.env.EMAIL_HOST,
    port: process.env.EMAIL_PORT,
    auth: {
      user: process.env.EMAIL_USERNAME,
      pass: process.env.EMAIL_PASSWORD
    }
  });

  // 2) Define the email options
  const mailOptions = {
    from: 'Sanket Badjate <hello@jonas.io>',
    to: options.email,
    subject: options.subject,
    text: options.message
    // html:
  };

  // 3) Actually send the email
  await transporter.sendMail(mailOptions);
};

module.exports = sendEmail;

```

[Node farm](https://www.notion.so/Node-farm-cf77f121738b4e9f9c07c007cc578399)

[https://www.notion.so](https://www.notion.so)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2043.png)

Rate Limiting

`npm i express-rate-limit`

Data sanitize 

`npm I express-mongo-sanitize`

`npm i xss-clean`

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2044.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2045.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2046.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2047.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2048.png)

![Untitled](Node%20JS%203354e62e7a9547ba8d6d2e3405225515/Untitled%2049.png)
