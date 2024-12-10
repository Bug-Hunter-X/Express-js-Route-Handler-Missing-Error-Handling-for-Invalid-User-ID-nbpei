# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: the lack of error handling for invalid input.  Specifically, the `/users/:id` route attempts to parse the `id` parameter as an integer without checking if it's a valid number.  This can lead to unexpected behavior or crashes.

The `bug.js` file contains the buggy code, while `bugSolution.js` provides a corrected version with proper error handling.

## Bug
The primary issue lies in the lack of error handling when parsing the `userId`. If the `userId` is not a number (e.g., a string), `parseInt(userId)` will return `NaN`, leading to the `users.find` method failing to find the user even if a user with that ID exists.  This results in the application returning a 200 OK status with an empty response, rather than a proper 400 Bad Request error. 

## Solution
The `bugSolution.js` file addresses this by adding input validation and error handling.  It checks if `parseInt(userId)` results in `NaN` and sends a proper 400 Bad Request response in that scenario.