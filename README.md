# Node.js Server Hang Issue

This repository demonstrates a common issue in Node.js servers where the server appears to hang or become unresponsive after a long delay in processing a request.  The problem arises from blocking the event loop.

## Problem

The `bug.js` file contains a simple HTTP server.  It introduces a 5-second delay before sending a response. While seemingly innocuous, this blocks the event loop, preventing the server from handling other requests during this time.  If multiple requests come in during this 5 second delay, those requests could appear to never receive a response.

## Solution

The `bugSolution.js` file provides a corrected version, employing asynchronous operations and non-blocking practices to prevent the server from hanging.  The solution prevents the event loop from blocking while the delay is executed.

## How to Reproduce

1. Clone this repository.
2. Navigate to the repository directory.
3. Run `node bug.js`.
4. Open a browser and make requests to `http://localhost:3000` and observe the behavior.  If you make multiple requests quickly you will likely see that the requests seem to hang.
5. Repeat steps 3 and 4 with `node bugSolution.js` to see the difference.
