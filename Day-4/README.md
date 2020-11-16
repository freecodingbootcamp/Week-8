# Week-8 -- Day-4

## Endpoints

Commercial back end web development are all about endpoints! "What endpoint is it again?", "Can you create a new endpoint for searching all mini assets?", "Your search endpoint is missing the date field" etc. That is the type a talk you might here on a small web development team. Endpoints is what give the outside world access to your app. They are kind of like doors. And just like doors you might need a key to go through them. The doors give you access to the apps data. Depending on the door (endpoint) you enter you can update some data, retrieve some data, delete some data etc.
With endpoints you can have several different kind of frontends (ios app, android, website) but only one backend (api). This was something that was always confusing to me. I was always like "how does an ios app verion of let's say facebook and the web version access common data?" I always thought they would access the same data through two different types of endpoint sets (doors) but they don't have to! Having one backend with one api allows us to create several different kinds of frontend apps. Access to the api is very generic. It's not specific to a language or framework! That is important to understand. Think about it. Let's just look at an example:

    /* GET All messages */
    router.get('/all', function(req, res, next) {
      console.log("GET ALL MESSAGES ENDPOINT");
      res.json({messages: messages});
    });\

This endpoint is written in JavaScript and is running on a node.js / express server. You can write your endpoints with any valid backend language / framework you like. The above endpoint code is saying if someone is going to `/all` of you app's url they should get a json back with one key `messages`. So let's say you uploaded and running your app's backend with the domain: https://messageapp.com then visiting https://messageapp.com/all would return a json object that might look like this:

    {
    	messages: [{text: "Hey, you up?"},{text: "Yeah, whats up?"},{text: "nothing, u?"}]
    }


## Node / Express Put Endpoint

Here as example of a simple put end point:

    /* PUT Update message with the given id */
    router.put('/update/:id', function(req, res, next) {
      console.log("UPDATING a message");
      // Extract id from the URL
      let id = req.params.id;
      // Extract the incoming data
      let content = req.body;
      // Extract the text field from the incoming data
      let text = content.text;
      // Extract the user from the incoming data
      let user = content.user;
      // Initialize a return response object. We will send this back later.
      let response = {};

      // Iterate over messages and find the message with the given id
      for(let i = 0; i < messages.length; i++){
        // Current message we are iterating over
        let message = messages[i];
        // If the message id matches the id we got from the request URL it's a match
        if(message.id == id){
          // Set message content to updated values
          messages[i] = {text: text, user: user, added: message.added, id: id};
          // Set the response to the new updated value (optional)
          response = messages[i];
        }
      }

	  // Send back the updated message (optional)
      res.json(response);
    });

Notice how we made this endpoint a put statement not a get or post. Technically you don't have to do that. You could make updating "something" a get or post endpoint. The difference is a subtle. Here is how one guy tried to explain in an stackoverflow answer:

> POST and PUT are very similar in that they both send data to the
> server that the server will need to store somewhere. if you make the
> same request twice using PUT, with the same parameters both times, the
> second request will have no effect. This is why PUT is generally used
> for the Update scenario.


Hope this helped you understand endpoints a little better.
I recommend the following read:

https://www.sitepoint.com/developers-rest-api/

Don't skip it or stop reading even if it doesn't make complete sense yet.
