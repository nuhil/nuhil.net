+++
languageCode = "en-us"
title = "Make 10 HTTP Web Servers in Just 10 Minutes"
author = "Nuhil Mehdy"

date = 2017-11-18T00:00:00-00:00

categories = ["Tools"]
tags = ["Server", 
        "http", 
        "Node.js", 
        "SimpleHTTPServer", 
        "http.server", 
        "Ruby httpd", 
        "Gulp", 
        "Apache", 
        "macOS", 
        "Caddy"]

description = "I have demonstrated how you can quickly create HTTP web servers in 10 different ways! Using Chrome Extension, Python, Ruby, PHP, Node.js, Gulp, Caddy etc."
featured = ""
featuredalt = "server"
featuredpath = "//i.imgur.com/iz5DsaH.png"
linktitle = ""
type = "post"
+++

### 1. Chrome Web Server  
---
Visit this link and install the Chrome App - 
[Chrome Web Server](https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb?hl=en)    
Then launch the app and point out your desired directory from inside which you want to serve your content. Finally it will show you the ready URL something like this - 

http://127.0.0.1:8887   


### 2. Python 2  
---
You can use the Python2's built in module named `SimpleHTTPServer`. Just issue the following command in your terminal from inside your document directory.     

```python
python -m SimpleHTTPServer 8000
```  

And visit - 
http://localhost:8000  

Reference - [Python Official Website](https://docs.python.org/2/library/simplehttpserver.html)   


### 3. Python 3   
---   
You can also use the Python3's built in module named `http.server`. Just issue the following command in your terminal from inside your document directory -    

```python
python -m http.server
```    

And visit - 
http://localhost:8000   

Reference - [Python Official Website](https://docs.python.org/3/library/http.server.html)   

<!--more-->

### 4. PHP Built in Server  
---
If you are using PHP greater than 5.4 then just utilize it's built in server facility. Issue the following command from inside your document directory -   

```php
php -S localhost:8000
```   

And visit - 
http://localhost:8000/   

Reference - [PHP Official Website](http://php.net/manual/en/features.commandline.webserver.php)   


### 5. Ruby	httpd  
---
If you have Ruby installed in your computer and it is at-least 1.9 then just use the following command to boot up a quick HTTP server.  

```ruby
ruby -run -e httpd . -p 8000
```   

And visit - 
http://localhost:8000   

Reference - [Ruby Official Repository](https://github.com/ruby/ruby/blob/trunk/lib/un.rb#L313)   

### 6. Node.js Environment  
---
If you have `Node.js` installed in your system then you must have `npm` installed also. Then just install the `http-server` module by following command.     

```js
npm install http-server -g
```   

Then issue the following command to start up a server from inside your desired document or project directory -   

```sh
http-server
```   

And visit - 
http://localhost:8080   

Reference - [Official Documentation](https://www.npmjs.com/package/http-server)   

### 7. gulp.js   
---
As you have `Node.js` installed and may be want to use Gulp as task runner for front end development, then install the following modules by issuing commands like below (from inside your project directory) -    
```js
npm install gulp --save-dev
```   
```js
npm install gulp-connect --save-dev
```   

Then create a file named `gulpfile.js` inside your document root or project root which should contain the below code snippet.   

```js
var gulp = require("gulp"),
    connect = require("gulp-connect");

gulp.task("server",function(){
    connect.server({
        port:8888
    });
});

gulp.task("default",["server"]);
```   

Then issue the below command to boot up a quick HTTP web server -   

```js
gulp
```   

And visit - 
http://localhost:8888   

Reference - [Official Documentation](https://www.npmjs.com/package/gulp-connect)   

### 8. Default Apache of macOS
---   
If you are a macOS user then you should have Apache installed already by default. So, utilize that software by starting and stopping it by following commands -   

```sh
sudo apachectl start
```   
```sh
sudo apachectl stop
```   

And visit - 
http://localhost/   

> **Note** - the default document root for this tool is `/Library/WebServer/Documents`   

Reference - [Apple Discussion](https://discussions.apple.com/docs/DOC-12034)   


### 9. Ruby gem serve
---   
You can use a very good Ruby gem named `serve`. Just install it in your system using the below command -   

```ruby
gem install serve
```   

Then issue the following command from inside your document directory -   

```sh
serve
```  

And visit - 
http://localhost:4000/

Reference - [Official Documentation](https://rubygems.org/gems/serve/versions/1.5.2)    


### 10. Caddy
---   
You can use a production ready web server quickly by installing the `caddy` software by following command -   

```sh
curl https://getcaddy.com | bash -s personal
```   

Then issue the below command from inside your document directory -   

```sh
caddy
```   

And visit - 
http://localhost:2015/   

Reference - [Official Website](https://caddyserver.com/)   


### Video Demonstration   
{{< youtube Kw_iEKjunRw >}}   
