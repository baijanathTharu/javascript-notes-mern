# Promises in JavaScript

## Drawback in Callbacks

- Callbacks can be invoked any number of times inside the function
- Thus, the state of the result of the task keeps on changing.

- Example:

```js
function sendMail(details, callBack) {
  setTimeout(function () {
    // callBack is invoked thrice
    // and result of task keeps on changing which should not happen
    // So there is need of promises which helps to prevent this behavior.
    callBack(null, "Done"); // task is completed
    callBack("Error", null); // task could not complete
    callBack("Error"); // task could not complete
  }, 2000);
}

sendMail({ id: 1, email: "test@test.com" }, function (err, done) {
  if (err) {
    console.log("Error: ", err);
  } else {
    console.log("Success: ", done);
  }
});
```

## What is a Promise?

- Promise is an object which will have the values of future result fetched after asynchronous call.

## State of a Promise

- Pending State: promise is created or initial state.
- Fulfilled State: operation is completed successfully.
- Rejected State: operation failed.

  > When the state has reached any one of fulfilled or rejected state, the promise is said to be settled.

## Three Methods in Promise

- **then:** handles success and error both
- **catch:** handles rejection
- **finally:** this method is executed when the promise has settled.

## Promise Examples:

- fetchEmail is a promise which is assigned a task to fetch email.

* **Example1: Promise is fullfilled**

```js
var fetchEmail = new Promise(function (success, failure) {
  // argument success is a placeholder for success callback
  // argument failure is a placeholder for failure callback
  setTimeout(function () {
    success({
      id: 1,
      email: "test@test.com",
    });
  }, 2000);
});

fetchEmail
  .then(function (data) {
    console.log("Promise is fulfilled: ", data);
  })
  .catch(function (err) {
    console.log("Promise is rejected: ", err);
  })
  .finally(function () {
    console.log("Promise is settled.");
  });
});
```

- **Example2: Promise is rejected**

> Note: it is common to name success as resolve and failure as reject.

```js
var fetchEmail = new Promise(function (resolve, reject) {
  setTimeout(function () {
   reject('Network connection failed');
  }, 2000);
});

fetchEmail
  .then(function (data) {
    console.log("Promise is fulfilled: ", data);
  })
  .catch(function (err) {
    console.log("Promise is rejected: ", err);
  })
  .finally(function () {
    console.log("Promise is settled.");
  });
});
```

- **Example3: Nested Promises**

```js
var takePhoto = function () {
  return new Promise(function (resolve, reject) {
    setTimeout(function () {
      resolve("Photo taken successfully...");
    }, 2000);
  });
};

var editPhoto = function () {
  return new Promise(function (resolve, reject) {
    setTimeout(function () {
      resolve("Photo edited successfully...");
    }, 2000);
  });
};

var uploadPhoto = function () {
  return new Promise(function (resolve, reject) {
    setTimeout(function () {
      // resolve('Photo uploaded successfully...');
      reject("Error while uploading...");
    }, 2000);
  });
};

// Execution
// first take photo
console.log("Take photo before editing...");

takePhoto()
  .then(function (data) {
    console.log("Data:>> ", data);
    // now edit photo
    editPhoto()
      .then(function (data) {
        console.log("Data:>> ", data);
        // now upload photo
        uploadPhoto()
          .then(function (data) {
            console.log("Data:>> ", data);
          })
          .catch(function (err) {
            console.log("Error:>> ", err);
          })
          .finally(function () {
            console.log("Promise for uploading photo is settled.");
          });
      })
      .catch(function (err) {
        console.log("Error:>> ", err);
      })
      .finally(function () {
        console.log("Promise for editing photo is settled.");
      });
  })
  .catch(function (err) {
    console.log("Error:>> ", err);
  })
  .finally(function () {
    console.log("Promise for taking photo is settled.");
  });

console.log("Performing some non blocking taks....");
```
