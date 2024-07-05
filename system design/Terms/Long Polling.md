**Long Polling**: Although less efficient than WebSockets, long polling can also be used. With long polling, the client sends a request to the server, and the server holds the request open until new data is available or a timeout period expires. This method simulates a persistent connection and can be effective in environments where WebSockets are not supported or practical

Long polling is like having muliple connection requests but server wont send response until the response is ready from server side (this can be achieved because we have keep-alive time in request header which can be configured accordingly)


