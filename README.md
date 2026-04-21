## Commit 1 Reflection notes

In this milestone, the `handle_connection` function is responsible for reading the incoming TCP stream. It wraps the stream in a `BufReader` to buffer the reads, making it more efficient than reading byte by byte. The code then reads the incoming HTTP request line by line, mapping each result and stopping when it encounters an empty line, which signifies the end of the HTTP request headers. The collected lines are then printed to the console so we can inspect the raw HTTP request sent by the browser.

## Commit 2 Reflection notes

The updated `handle_connection` function now actively responds to the client instead of just printing the request. It constructs a valid HTTP response by defining a status line (`HTTP/1.1 200 OK`) and reading the contents of `hello.html` into a string. It then calculates the byte length of the HTML content to set the `Content-Length` header. Finally, it formats these components into a standard HTTP response string and writes it back to the TCP stream as bytes, allowing the browser to render the HTML page. 

![Commit 2 screen capture](assets/images/commit2.png)

