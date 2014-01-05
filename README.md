#Node.js Scalable Framework

##Don't Know Node.js?
  * start here: http://stackoverflow.com/questions/1884724/what-is-node-js    

##Usage Module

###Node.js lib
* [connect](https://github.com/senchalabs/connect) = http connect framework for node -> plugins aka middleware 
* [express](http://expressjs.com/)  = connect base framework for build web-app
* [passport](http://passportjs.org/) = connect middleware for auth
* [mongoose](http://mongoosejs.com/) = mongo object mapping
   * [mongoose dbref](https://github.com/goulash1971/mongoose-dbref) - plugin to enable mongoose use dbref type
* [nconf](https://github.com/flatiron/nconf) = provide config file
* [kraken](http://krakenjs.com/) = express base framework for writing scalable application
   * completed security (can closed for dev-env)
   * using nconf for manage config due to ~ NODE_ENV
      * development: /^dev/i,
      * test       : /^test/i,
      * staging    : /^stag/i,
      * production : /^prod/i 
* [recluster](https://github.com/doxout/recluster) = provide node cluster and automatic restart failure worker

###Other
   * [nginx](http://blog.argteam.com/coding/hardening-node-js-for-production-part-2-using-nginx-to-avoid-node-js-load/) - recommend http server for serve static file instead using node


## Directory structure
- **/config** - Application and middleware configuration
- **/controllers** - Controllers
- **/lib** - Custom developer libraries and other code
- **/locales** - Local-based content
- **/models** - Models
- **/public** - Web resources that are publicly available
- **/public/templates** - Server and browser-side templates
- **/tests** - Unit and functional test cases

## Configuration

Configuration is stored in JSON format. Each settings file can be overridden in development mode by creating a `-development` version, e.g. app-development.json.

- **/config/app.json** - Application specific settings
- **/config/middleware.json** - Custom middleware specific settings

### Using custom configuration
If you'd like to add your own configuration to these files, simply include a new key.
To retrieve it in your application, you can do so during the configuration step

### Default Values
Visit https://raw.github.com/paypal/kraken-js to lookup default value

##Install and Use
###Install
 1.  pull this repository
 2. go to project folder and exec command
``` 
npm install
```

###Run Node
* Normal (It’s will run in development by default)
  ```          
  node index
  ```
* Automatic Reload when file change
 1. install supervisor with administrator permission (sudo on unix) ``` npm install supervisor -g```
 2. use supervisor term instead of node ```supervisor index```
* Run node in Production env by ```NODE_ENV=PRODUCTION node index```
* Run node in other env where env is [‘development’, ’test’, ’staging’, ‘production’]
   * ```NODE_ENV={env} node index```

##DEBUG 

  How to debug in this project
  
###Logger
  
  color logger with more information than console.log
  
  more detail https://github.com/baryon/tracer
  ```
  var logger = require('./lib/logger');
  then use
    * logger.log - color black bold
    * logger.info - color green
    * logger.error - color red bold
    * logger.warn - color orange
    * logger.debug - color blue
    * logger.trace - color magneta
  ```

###Break Point
####Debug with Chrome using NodeInspector
```
1. Install it globally: npm install -g node-inspector
2. Run your app in debug mode: node --debug-brk your/node/program.js
3. In another terminal window run node-inspector: node-inspector
4. Open http://127.0.0.1:8080/debug?port=5858
```
ref: https://github.com/node-inspector/node-inspector

####Debug with Webstrom
http://www.jetbrains.com/webstorm/webhelp/running-and-debugging-node-js.html

####Ref and More Debug Technique
http://stackoverflow.com/a/16512303

##Todos

  * add test doc
  * add exception handler doc
  * add mongoose and mongoose dbref plugin doc
  * add s3 doc
  * add auth doc
  * add table of content
  
##Reference

####What Why and When to Use NodeJS
   * http://stackoverflow.com/questions/2353818/how-do-i-get-started-with-node-js
   * http://stackoverflow.com/questions/5062614/how-to-decide-when-to-use-nodejs
   * http://stackoverflow.com/questions/1884724/what-is-node-js    
   * http://blog.nelhage.com/2012/03/why-node-js-is-cool/
   * http://stackoverflow.com/questions/5599024/what-so-different-about-node-jss-event-driven-cant-we-do-that-in-asp-nets-ht

####Use Case
   * https://engineering.groupon.com/2013/node-js/geekon-i-tier/
   * http://www.twilio.com/blog/2012/09/building-a-real-time-sms-voting-app-part-1-node-js-couchdb.html
   * http://www.nczonline.net/blog/2013/10/07/node-js-and-the-new-web-front-end/
   * https://www.paypal-engineering.com/2013/11/22/node-js-at-paypal/
   * http://www.slideshare.net/lennymarkus/node-js-at-paypal
   * http://www.slideshare.net/billwscott/kicking-up-the-dust-with-node-js
   * http://www.slideshare.net/billwscott/clash-of-the-titans-releasing-the-kraken-nodejs-paypal
   * http://engineering.linkedin.com/tags/nodejs

####Node.JS In production
   * http://www.slideshare.net/BenLin2/webconf-nodejsproductionarchitecture
   * http://www.slideshare.net/iloire/building-web-apps-with-nodejs-socketio-knockoutjs-and-zombiejs-codemotion-2012
   * http://www.slideshare.net/RyanRoemer/seanode-prodtalk?from_search=5
   * http://blog.argteam.com/coding/hardening-node-js-for-production-part-2-using-nginx-to-avoid-node-js-load/
   * http://www.theorganicagency.com/apache-vs-nginx-performance-comparison/
   * http://sandinmyjoints.github.io/towards-100-pct-uptime

####Performance + Memory Management
   * https://hacks.mozilla.org/2012/11/tracking-down-memory-leaks-in-node-js-a-node-js-holiday-season/
   * http://www.webreference.com/programming/javascript/jkm3/index.html
   * https://www.scirra.com/blog/76/how-to-write-low-garbage-real-time-javascript
   * https://github.com/c4milo/node-webkit-agent

####Exception Handler
   * http://stackoverflow.com/questions/7310521/node-js-best-practice-exception-handling
   * https://github.com/isaacs/node-supervisor
   * https://github.com/nodejitsu/forever

####Debug 
   * http://stackoverflow.com/questions/1911015/how-to-debug-node-js-applications

####Pattern
   * http://shichuan.github.io/javascript-patterns/
   * http://stackoverflow.com/questions/5495984/coding-style-guide-for-node-js-apps

####KrakenJS Scalable layer that extends Express by providing structure and convention (By Paypal)
   * http://krakenjs.com/
   * https://github.com/paypal/generator-kraken
   * https://github.com/paypal/kraken-devtools
   * https://github.com/paypal/express-enrouten

####Nginx
   * http://stackoverflow.com/questions/9967887/node-js-itself-or-nginx-frontend-for-serving-static-files
   * http://stackoverflow.com/questions/5530784/node-js-server-to-return-static-files-from-public-via-nginx?rq=1
   
####Other
   * https://github.com/joyent/node/wiki/modules
   * http://stackoverflow.com/questions/10695629/node-js-express-next
   * http://stackoverflow.com/questions/5311334/what-is-the-purpose-of-nodejs-module-exports-and-how-do-you-use-it
   * http://passportjs.org/
   * http://llun.in.th/cards/2013/6/OAuth2%20server%20with%20node.js.html#/view/th
   * http://stackoverflow.com/questions/4706020/bdd-and-tdd-for-node-js
   * http://stackoverflow.com/questions/5009324/node-js-nginx-and-now
   * https://github.com/flatiron/nconf   
   * http://mongoosejs.com/
   * https://github.com/substack/node-password-reset
   * https://npmjs.org/package/yocrud
   * http://mmonit.com/monit/
   * http://rowanmanning.com/posts/node-cluster-and-express/
   * http://zombie.labnotes.org/
