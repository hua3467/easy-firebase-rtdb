This is a helper class that help you read and write Firebase realtime database easily.

## Realtime Database Configuration

1. Before loading this class, you must add Firebase cdn in your HTML document:

```html
<script src="https://www.gstatic.com/firebasejs/7.19.0/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/7.19.0/firebase-database.js"></script>
```

2. Add this library in two ways:
- Go to [https://github.com/hua3467/easy-firebase-rtdb/],  download `Database.js` or `Database@0.2.js`, and attach to your page,
- Use https://hua3467.github.io/easy-firebase-rtdb/Database@0.2.js.

3. insert your web app's Firebase configuration

```javascript
const firebaseConfig = {
  apiKey: "your-api-Key",
  authDomain: "your-project-id.firebaseapp.com",
  databaseURL: "https://your-project-id.firebaseio.com",
  projectId: "your-project-id",
  storageBucket: "your-project-id.appspot.com",
  messagingSenderId: "{}",
  appId: "{}",
  measurementId: "{}"
};
```

Example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script src="https://www.gstatic.com/firebasejs/7.19.0/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/7.19.0/firebase-database.js"></script>
    <script src="https://hua3467.github.io/easy-firebase-rtdb/Database@0.2.js"></script>
    <script>
      const firebaseConfig = {
          apiKey: "your-api-Key",
          authDomain: "your-project-id.firebaseapp.com",
          databaseURL: "https://your-project-id.firebaseio.com",
          projectId: "your-project-id",
          storageBucket: "your-project-id.appspot.com",
          messagingSenderId: "{}",
          appId: "{}",
          measurementId: "{}"
        };
    </script>
    
</body>
</html>
```

## Usage

### Initiate a Database object

Enter `""` if you want to access the root node.

```javascript
const db = new Database("test/childnode", firebaseConfig);
```

*Example*:

```javascript
const db = new Database("", firebaseConfig);
```

### Read data

```javascript
db.read("the path of the node you want to read", data => {
    console.log(data);
});
```

*Example*:

```javascript
db.read("", data => {
    console.log(data);
});

db.read("childnode-2", data => {
    console.log(data);
});
```

### Listen to a node

```javascript
db.onDataUpdated("the path of the node you want to listen", data => {
    console.log(data);
});
```

*Example*:

```javascript
db.onDataUpdated("childnode-2/location", data => {
    console.log("Location updated: ", data);
});
```

### Set the value of a node

```javascript
db.set("the path of node you want to update", value);
```

*Example*:

```javascript
db.set("childnode-2/location", "12");
```

### update a node

```javascript
db.update("the path of node you want to update", object_or_value, [callback]);
```

*Example*:

```javascript
db.update("childnode-2/info", {
    time: "12:20pm",
    name: "Aaron",
    location: [98.3134, 104.3984]
}, () => {
    console.log("done");
});
```

### Append data into a node

```javascript
db.append("the path of node you want to add", data);
```

*Example*:

```javascript
db.append("childnode-2/list", {
    title: "New Title",
    author: "Aaron"
});
```
