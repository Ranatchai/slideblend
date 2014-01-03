#Slideblend-Node.js
look up for pretty format at https://github.com/Ranatchai/slideblend
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
To retrieve it in your application, you can do so during the [configuration step](#application-life-cycle-middleware)

### Default Values
Visit https://raw.github.com/paypal/kraken-js to lookup default value

##nodejs lib

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
https://github.com/node-inspector/node-inspector
```
1. Install it globally: npm install -g node-inspector
2. Run your app in debug mode: node --debug-brk your/node/program.js
3. In another terminal window run node-inspector: node-inspector
4. Open http://127.0.0.1:8080/debug?port=5858
```
####Debug with Webstrom
see detail at http://www.jetbrains.com/webstorm/webhelp/running-and-debugging-node-js.html

  __Ref and More Debug Technique:__ http://stackoverflow.com/a/16512303

##Other

   * [nginx](http://blog.argteam.com/coding/hardening-node-js-for-production-part-2-using-nginx-to-avoid-node-js-load/) - recommend http server for serve static file instead using node

##Install and Use

   * __Install__
        1.  pull this repository
        2.  go to project folder and exec command
            ``` 
            npm install
            ```
   * __Run Node__
      * Normal (It’s will run in development by default)
        ```          
        node index
        ```
      * Run node in {env} where {env} is [‘development’, ’test’, ’staging’, ‘production’]
         * NODE_ENV={env} node index 
         * ex: 
        ``` 
        NODE_ENV=PRODUCTION node index 
        ```
