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

### Example 1:

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

### Example 2:

```js
function verifyUser(user, callBack) {
  console.log(user, " wants to log in.");
  console.log("Sending OTP...");
  setTimeout(function () {
    // callBack('OTP incorrect', null);
    callBack(null, "successfully");
  }, 2000);
}

verifyUser("Ram", function (err, done) {
  if (err) {
    console.log("Error: ", err);
    console.log("Please enter the OTP correctly.");
  } else {
    console.log("You are logged in ", done);
    console.log("Now you can upload files.");
  }
});

console.log("performing non blocking tasks...");
```

## Bigger picture of Callback. (error or success)

- Callback can be used to handle the result of asynchronous call by checking error or success.

* In the example below, we try to handle the result of _editPhoto_.

### Example 1:

```js
/* Task Part */
function uploadPhoto(photoName, callBack) {
  console.log("Uploading ", photoName, "...");
  setTimeout(function () {
    callBack(null, "Upload Successful.");
  }, 2000);
}

function editPhoto(photoName, callBack) {
  console.log("Editing ", photoName, "...");
  setTimeout(function () {
    callBack(null, "Editing Successful.");
  }, 2000);
}

function downloadPhoto(photoName, callBack) {
  console.log("Downloading ", photoName, "...");
  setTimeout(function () {
    // callBack(null, 'Downloading Successful');
    callBack("Downloading failed.", null);
  }, 2000);
}

/* Task Part end */

/* Execution Part */
console.log("Photo Editing Web App");
uploadPhoto("myProfile.png", function (err, done) {
  if (err) {
    console.log("Error: ", err);
  } else {
    console.log("Complete: ", done);
    editPhoto("myProfile.png", function (err, done) {
      if (err) {
        console.log("Error: ", err);
      } else {
        console.log("Complete: ", done);
        downloadPhoto("myProfile.png", function (err, done) {
          if (err) {
            console.log("Error: ", err);
          } else {
            console.log("Complete: ", done);
          }
        });
      }
    });
  }
});

console.log("Performing some non blocking tasks");
/* Execution Part end */
```
### Example2: Important
```js
// tasks
// take photo first
// edit photo
// upload photo

function takePhoto(photo, callback) {
  setTimeout(function(){
    callback(null, 'Photo Taken successfully...');
  }, 2000)
}

function editPhoto(photo, callback){
  setTimeout(function(){
    // callback(null, 'Photo edited successfully...');
    callback('Editing is failed', null);
  }, 200);
}

function uploadPhoto(photo, callback) {
  setTimeout(function() {
    callback(null, 'Photo uploaded successfully...');
  }, 2000);
}


// Executions
console.log('Take a photo before editing...');

takePhoto('profile.png', function(err, done) {
  if(err) {
    console.log('Error: ',err);
  } else {
    console.log('Result: ', done);
    // edit photo now
    editPhoto('profile.png', function(err, done) {
      if(err) {
        console.log('Error: ', err);
      } else {
        console.log('Result: ', done);
        // now upload the photo
        uploadPhoto('profile.png', function(err, done) {
          if(err) {
            console.lgo('Error: ',err);
          } else {
            console.log('Result: ', done);
          }
        })
      } 
    })
  }
})

console.log('Performing some non blocking tasks...');
```