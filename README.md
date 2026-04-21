## Commit 1 Reflection notes

In this milestone, the `handle_connection` function is responsible for reading the incoming TCP stream. It wraps the stream in a `BufReader` to buffer the reads, making it more efficient than reading byte by byte. The code then reads the incoming HTTP request line by line, mapping each result and stopping when it encounters an empty line, which signifies the end of the HTTP request headers. The collected lines are then printed to the console so we can inspect the raw HTTP request sent by the browser.

## Commit 2 Reflection notes

The updated `handle_connection` function now actively responds to the client instead of just printing the request. It constructs a valid HTTP response by defining a status line (`HTTP/1.1 200 OK`) and reading the contents of `hello.html` into a string. It then calculates the byte length of the HTML content to set the `Content-Length` header. Finally, it formats these components into a standard HTTP response string and writes it back to the TCP stream as bytes, allowing the browser to render the HTML page. 

![Commit 2 screen capture](assets/images/commit2.png)

## Commit 2 Reflection notes

The refactoring in this milestone introduces routing to our web server. By reading just the first line of the HTTP request, the server can determine exactly what the client is asking for. We use an `if/else` block (or `match`) to check if the request line is exactly `GET / HTTP/1.1`. If it is, the server responds with the `200 OK` status and the `hello.html` file. For any other request, it selectively responds with a `404 NOT FOUND` status and a `404.html` error page. This split is necessary so that the server behaves correctly according to HTTP standards, rather than blindly returning the same page regardless of the requested URL.

![Commit 3 screen capture](assets/images/commit3.png)