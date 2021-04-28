# Reading Notes
## Class 13
_____________________________________________________________________________________________________________________________________


### Status Codes Based On REST Methods

In your own words, describe what each group of status code represents:
100’s =  header part of the request has been received and the server will try to comply with a transmission demand of the client
200’s = tell the client that its request was accepted
300’s = tell the client that the resource they are requesting isn’t available at the expected location anymore
400’s = invalid requests a client sent to a server casued by timeouts, wrong URI, missing authentication, etc
500’s = server error codes

What is a status code 202? - doesn’t mean the request was successfully processed only that it met all validation requirements at the time of sending
What is a status code 308? -  This tells the client to use another URL to access the resource and not use the current URL anymore
What code would you use if an update didn’t return data to a client? - 204
What code would you use if a resource used to exist but no longer does? - 308
What is the ‘Forbidden’ status code? - 403


(Build A REST API With Node.js, Express, & MongoDB - Quick)[https://www.youtube.com/channel/UCFbNIlppjAuEX4znoulh0Cw]

Why do we need to pull our MongoDB database string out of our server and put it into our .env? - So that it is hidden from git
What is middleware? all the code that runs before the final route call back.
What does app.use(express.json()) do? lets the server except json as a body
What does the /:id mean in a route? that is how we recieve parameters
What is the difference beween PUT and PATCH?
How do you make a defalut value in a schema?
What does a 500 error status code mean?
What is the difference between a status 200 and a status 201?
