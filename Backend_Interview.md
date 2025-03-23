### CDN (Content Delievery Network)


- Distributed servers that deliever web content to users based on their geographical location.
- Stored on multiple servers in various locations.
- Routes the request to the server closest to the user.
- Faster than getting this from the origin server.
- CDN has two types of server :- 
     1. Origin Server
     2. Edge Srever (Content copied to edge server from origin server)

### Web Request

- The Browser sends a request to the DNS server to resolve the domain name of the URL to its corresponding IP address.

- The DNS server returns the IP address of the closest CDN edge server to the user's location.

- e.g. somebody search www.google.com in thailand get the edge server location cloaset to it.

- Then CDN edge server checks its cache. If found in cache, the CDN edge server returns the cached version.

- Then CDN edge server checks its cache. If not found in cache, the CDN edge server sends request to the origin server.


### DNS 

- Aliasing system to IP addresses

### A Web Page

- HTML page
- CSS assets
- Images
- Javascript assests
- Fonts


## BROWSER                 CDN                    BACKEND APP
     
            Load Page
     |--------------------->|
     | Send HTML, CSS, JS   |
     |<---------------------|
     
     | Render HTML and execute JS
     |-----|
     |<----|                                            
                       JS Makes API calls               
     |------------------------------------------------->|
     |                                                  |
     |                   API Responses                  |
     |<-------------------------------------------------|


### REST API Request Flow (REST requests)

What happens to browser when rest request happens? 

- JavaScript code constructs an HTTP request object. To the request object it adds endpoint API URL and HTTP method.
- The Javascript code needs to know what's the URL where the request is being accessed.
- URL is going to go to the DNS. DNS is going to map name to IP address.
- Includes necessary parameters or data in request body.
- Server gets request and returns a response
- JavaScript recieves response and processes it.
- Response manifests as a UI change.

### HTTP (Hyper text transfer protocol)

It's a protocol for sending request over the internet.
A message sent by a client (such as a web browser) to a server to request specific information.

- **HTTP Request consists of:-**

- 1st line - Request Line (GET/index.html HTTP/1.1)
- 2nd line - Meta info about the request
- 3rd line - Body (Data to be sent with the request)

GET /index.html HTTP/1.1      
Host           : www.example.com                          -----------> Headers
User-Agent     : Mozilla/5.0 (Windows NT 10.0; Win64; x64)-----------> Headers
Accept-Language: en-US,en;q=0.5                           -----------> Headers
Accept-Encoding: gzip, deflate                            -----------> Headers
Connection     : keep-alive                               -----------> Headers

- **HTTP Response consists of:-**

- Status line: First Line Eg: `HTTP/1.1 200 OK`
- Headers    : Meta information about the response
- Body       : Actual Data being sent. 

HTTP/1.1 200 OK
Date   : Mon, 01 Feb 2023 12:00:00:00 GMT      ----> headers
Server : Apache/2.4.46 (Ubuntu)                ----> headers
Last-Modified : Mon, 01 Jan 2023 12:00:00 GMT  ----> headers
Content-Type :  text/html; charset=UTF-8
Content-Length: 57
Connection: keep-alive

<html>
   <head>
     <title>Example Page</title>
   <head>
     <body>
     </body>
</html>


### Http is a stateless protocol

- You cannot refer to a previous request in any request.
- Every request should be self sufficient and standalone.

### Cookies

- Cookies is a mechananism to allow multiple HTTP requests to be "tied together".
- It is initiated by the server. The server can create a cookie on client machine.
- It's like a marker/bookmark.
- Solution to Problem when we have login and we need to remember the particular
  user the next time they made a request.
- To do that in a response the server sends a cookie.
- It is sent to the client in the Set-Cookie header of a response by the server.
- Then automatically the client sends the cookie in the cookie header in every subsequent request of that domain.
- Useful for server sessions like Login Flow.

### Login Flow

- User enters login credentials into a web form.
- Form data is submitted using HTTP POST.
- Server verifies the credentials.
- Server generates a new session for the user.
- Server creates a unique token (Session ID)
- Server sends the Session ID back with the response with (Set-Cookie=Session ID) in header.
- Browser stores the cookie on the user's device because it has be saved somewhere.
- Next time when browser sends the request it also send the cookie in Cookie header.
- Server looks up the session info (Session ID) based on the list of session ID it has 
  and if it recognize the user by pulling the session IDs, then server can generate a 
  personlised response.
- **Benefit of cookie is that it is Automatic.**

### Diff b/w web server and app server

- Web server is something that host static content (HTML/CSS/JAVASCRIPT).
- App server is something that runs code (not just the assets).
- It can be used interchangeably.

### Diff b/w services and applications

- An application is ususally something that forms one thing like one app (facebook,google search)
- Services are someting that work together to form an application.

### Source Control

- **Git** is a distributed version control system for tracking changes in files and
  coordinating work among multipe people. 

- Keeps track of different versions of your code.
- Collaborate with others.
- Revert Back the previous versions if needed.
- Resolve Conflicts when multiple people are working on same codebase.

- **GitHub** is a web based platform that provides hosting and managing for Git repositories.

- Git manages versions of your code locally or on a remote servers.
- Github potential "main" remote server.

- **Features**

- pull requests
- issues
- wikis
- project management
- discussions
- actions              -> runs on every commit

- **Pull Request Workflow**

- Fork the repository   ->  Creates the copy of remote repo on your github account 
- Clone the repository  ->  Getting the forked repo on github on local machine
- Create a new branch   ->  On local machine and make your changes
- Push the changes      ->  
- Create a pull request ->  Requsting other person to pull my changes 
- Review and Discuss
- Merge or Decline
- Update or Delete the branch

- **Rebase** it's like keeping your changes aside and getting latest changes
from remote repo and addin your changes on top of that.


### Github WorkFlow

```java

   Open Source        Pull Request       Your Repo
 ---------------  <--------------------  ----------
 |owner of Repo|  ---------------------> |  Repo  |  NOT a clone 
 ---------------          Fork           ----------
                                          |    /|\
                                  clone   |     |   push
                                         \|/    |
                                         ----------    
                                         |  Repo  | 
                                         ----------
```

