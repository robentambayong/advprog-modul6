## Commit 1 Reflection notes

In this milestone, the handle_connection function is responsible for reading the incoming TCP stream. It wraps the stream in a BufReader to buffer the reads, making it more efficient than reading byte by byte. The code then reads the incoming HTTP request line by line, mapping each result and stopping when it encounters an empty line, which signifies the end of the HTTP request headers. The collected lines are then printed to the console so we can inspect the raw HTTP request sent by the browser.

