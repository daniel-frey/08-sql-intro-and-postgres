# Code 301: Testing PostgreSQL Setups

## First, Some Context...

Setting up and maintaining a dev environment is not always as simple and straightforward as we would like it to be. There are different operating systems on different machines in different versions... and then the tooling is different across different platforms, and the tools go through versions, too. Not only that, but most tools are stitched together with a patchwork of dependencies that often themselves have dependencies, and all of the pieces go through independent versioning processes.

So why do we go through this trouble? Consider a basic MVC pattern, with an end user's **View** being a representation of data from a **Model** that is acquired via a **Controller** layer of the WRRC (Web Request Response Cycle). In a real-world context, it is typical that each of the MVC components is an independent process (or, "application", or even "a program" if you want to call it that) running on its own machine in its own physical location, all communicating over networks.

On our laptops, we create a local mock-up of that process so that we can build web applications that will work in those interrelated environments:

- **View**: This runs in our browser
- **Controller**: This is our `server.js` running in Node in a tab in our terminal
- **Model**: This is the PostgreSQL application that is running in the background on our laptops; we can access it directly by running a SQL shell in a separate tab in our terminal.

Thus, you are frequently going to have at least three terminal tabs (or windows) open at once while building these kinds of applications:

- One for your interface to your file system and running Git commands
- One for Node to run your server
- One for `psql` to access your SQL shell so that you can interface directly with your database

Your skills in maintaining your dev environment are as much a part of your productivity as a developer as is the actual writing of code. Consider yourself a chef: in addition to creating tasty food, you must maintain your kitchen... with supplies readily available and fresh, knives sharpened, stove and oven working properly, all pots and pans and utensils you need cleaned and on hand, and command of your recipes, all of which have idiosyncracies depending upon atmospheric conditions *(ever try making fudge on a rainy day, or baking a cake at altitude?)* PLUS the preferences of your client. You simply can't use from-the-box macaroni-and-cheese with orange powder for everything.

## PostgreSQL Configuration

Setup and testing instructions for your PostgreSQL installation are in the [Code 301 Prework](https://github.com/codefellows/code-301-prework). If you haven't already, read and follow those steps carefully. 

### Connecting to your database

For working in our codebase, we will need to supply the `server.js` file a variable called `conString` that will facilitate the connection between the server and the database.

- Format: 
    
    `const conString = 'postgres://USER:PASSWORD@HOST:PORT/DBNAME'`
- Example: 
    
    `const conString = 'postgres://postgres:1234@localhost:5432/postgres'`
- On macOS, your username and password __should__ be automatically provided, so you can simplify: 
    
    `const conString = 'postgres://localhost:5432'`

