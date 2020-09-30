# Callback in JavaScript

## Synchronous Execution

- Step n waits for the result of step n-1.

### Advantages

- Readable code base.
- Easy to implement logic.

### Disadvantages

- Slow Execution

## Asynchronous Execution

- Step n do not wait for the result of step n-1.

* Result handling is a challenge with blocking task.

### Advantages

- Fast execution for (independent or non blocking tasks).

### Disadvantages

- Difficulty in implementing logic.
- Slightly unreadable codebase.

## Role of Callback in Handling Result

- Callback is a function which is passed as an argument to another function.
- Callbacks are used for handling the result of asynchronous call.

### Example:

```js
// here uploadVideo is a Higher order function.
function uploadVideo(videoName, callBack) {
  console.log("I have to upload ", videoName, " but there is no power.");
  // making delay for emulating async behavior
  setTimeout(function () {
    console.log("The power is back.");
    callBack();
  }, 2000);
}

uploadVideo("react-video.mp4", function () {
  // performing blocking tasks in the callback
  console.log("Now you can upload the video.");
});

// Non blocking tasks can be performed.
console.log("Shoot another video.");
console.log("Have your lunch.");
```

## Bigger picture of Callback. (error or success)

- Callback can be used to handle the result of asynchronous call by checking error or success.

* In the example below, we try to handle the result of _editPhoto_.

### Example:

```js
// Task Part::>>
function editPhoto(rawPhoto, callback) {
  console.log("Uploading ", rawPhoto, "...");
  // emulating asynchronous behavior
  setTimeout(function () {
    // error or success
    callback(null, "Success");
  }, 2000);
}
// !Task Part::>>

// Execution Part::>>CASE: ERROR OCCURS
console.log("I want to edit photo.");
editPhoto("profile.png", function (error, done) {
  console.log("Result of editPhoto::>>");
  if (error) {
    console.log("Uploading failed!");
    console.log("Editing: ", error);
  } else {
    console.log("Uploaded successfully!");
    console.log("Editing: ", done);
  }
});
// performing some non blocking tasks
console.log("Shoot another photo.");
console.log("Watch youtube videos.");
// !Execution Part::>>
```
