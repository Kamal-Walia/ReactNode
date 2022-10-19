# React + Node simple setup
1) create a folder
2) cd into that folder and run `npm init -y`
3) run `npm i express`
4) create another folder name it something like server
5) create index.js file in that folder and add the below code in that
```
// server/index.js

const express = require("express");

const PORT = process.env.PORT || 3001;

const app = express();

app.listen(PORT, () => {
  console.log(`Server listening on ${PORT}`);
});
```
6) In package.json add this in the script block
```
  "start": "node server/index.js"
```
7) To confirm everything is workin till now run `npm start` and visit `http://localhost:3001/api` you should see the message from server.

8) Create an endpoint in index.js file of your backend project
```
app.get("/api", (req, res) => {
  res.json({ message: "Hello from server!" });
});
```

9) Restart your node server

10) Create frontend application using `npx create-react-app client`

11) Add proxy in package.json of frontend project
```
"proxy": "http://localhost:3001",
```

12) Now we can call our API inside our react project like this:-
```
React.useEffect(() => {
    fetch("/api")
      .then((res) => res.json())
      .then((data) => setData(data.message));
  }, []);
```

