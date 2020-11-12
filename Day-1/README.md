# Week-8 -- Day-1

## Deploying Express to Heroku!

The name “**Heroku**” was created as a portmanteau of the words “hero” and “haiku.”
It could also just been invented and not mean anything prior to what it is today.

The way I look at Heroku is it allows up to host full-stack app relatively easy, fast, and not mention free.  There are other hosts out there but most of them cost money and might involve a slightly longer process to host for example a node / express app.

Let's get to it and host our simple messaging board app to Heroku. Actually, before I start I should talk a little bit about what hosting means. Hosting is just allowing your app to be accessed by the outside world, not just you. In order to achieve you would want some external server (computer) to hold your code and run the appropriate server, database services needed to run your app. So **now** let's get to it. We will be using the following two pages to get up and running with express on Heroku

https://www.theodinproject.com/courses/nodejs/lessons/preparing-for-deployment-nodejs
https://www.theodinproject.com/courses/nodejs/lessons/mini-message-board


### Create Github Repo First!

Make sure you create a Github repo and push your code to it before you continue with deploying to Heroku. Remember the steps to creating a Github repo? You go on Github.com, login, select create new repo and then follow the steps. Make sure NOT to select any of the checkmarks at the bottom of creating a new repo page. This way you will see the instructions on how to push to Github on the next page.


### Install Heroku Command Line Tool

Run the following command

```bash
curl https://cli-assets.heroku.com/install.sh | sh
```

Once the installation above is done check if node has been installed correctly:
Run

    heroku version

You should not get an error message.

### SSH Keys

Now add your SSH keys. Run:

```bash
heroku keys:add
```

Here you might run into some trouble. Just follow the instructions on the screen and you should be good. You can also do a google search: "add keys to Heroku on a mac"

### Modify package.json

Get your node version by running the following command:

    node --version

Take note of the version number.

Now add the following line to your package.json with the correct version number.

```json
"engines": { "node": "10.x.y" },
```

Please pay attention to the quotes and commas!

You might run into syntax errors. If that happens revisit the package.json file and make sure all commas are where they are supposed to be.

Here is how my package.json looks like:

       {
	      "name": "express-generator-app-ejs-default",
	      "version": "0.0.0",
	      "private": true,
	      "scripts": {
	        "start": "node app.js"
	      },
	      "dependencies": {
	        "cookie-parser": "~1.4.4",
	        "debug": "~2.6.9",
	        "ejs": "~2.6.1",
	        "express": "~4.16.1",
	        "http-errors": "~1.6.3",
	        "morgan": "~1.9.1"
	      },
	      "engines": {
	        "node": "14.15.0"
	      }
    }

### Test it Locally

Run the following command to see if your app runs locally:

```bash
heroku local web
```

If you don't run into any error messages you can proceed.

### Create Heroku Repo

Now run the following command to create a Heroku repo

```bash
heroku create
```

### Push to Heroku

Now you are ready to push your code to Heroku. Run the following command:

```bash
git push heroku main
```

You might have to change `main` to `master`

VERY IMPORTANT: if you didn't create a Github repo beforehand you might run into some issues. So make sure you created a Github repo and associate with your code before you try to push and deploy to Heroku.

Your app should now be trying to deploy your app. This process takes a minute. Look for the Heroku URL that ends in .com not .git and also the

> Build succeeded!

 statement.

Copy and paste the Heroku URL into your browser.

And Voila! You should see your app online. I remember how cool it felt having something you created on the web and accessible to everybody.
