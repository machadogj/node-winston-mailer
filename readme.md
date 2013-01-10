An email transport based on mailer for [winston][0].

## Installation

``` sh
  $ npm install winston
  $ npm install winston-mailer
```

## Usage
``` js
  var winston = require('winston');
  
  //
  // Requiring `winston-mailer` will expose 
  // `winston.transports.Mail`
  //
  require('winston-mailer').Mail;
  
  winston.add(winston.transports.Mail, options);
```

The Mail transport uses [mailer](http://github.com/Marak/node_mailer.git) behind the scenes.  Options are the following:


  /** buffering */
  this.maxBufferItems    = options.maxBufferItems         || 100;
  this.maxBufferTimeSpan = options.maxBufferTimeSpan      || 60 * 1000;
  this.buffer  = [];
  this.flushId = setTimeout(this.flush.bind(this), this.maxBufferTimeSpan);

  /** mailer options */
  this.opts  = {
    username        : options.username,
    password        : options.password,
    port            : options.port,
    host            : options.host,
    authentication  : 'login',
    to              : options.to,
    from            : options.from || "winston@" + os.hostname() + '.com',
    prefix          : options.prefix || '[winston]'
  };
* __to:__ The address(es) you want to send to. *[required]*
* __from:__ The 'from' address (default: `winston@[server-host-name].com`)
* __host:__ SMTP server hostname (default: localhost)
* __port:__ SMTP port (default: 587 or 25)
* __username__ User for server auth
* __password__ Password for server auth
* __level:__ Level of messages that this transport should log. 
* __silent:__ Boolean flag indicating whether to suppress output.
* __prefix:__ String for using in as prefix in the subject.
* __maxBufferItems__ Max errors that will be buffered (default 100)
* __maxBufferTimeSpan__ Max miliseconds errors will be buffered (default 60000)

[0]: https://github.com/flatiron/winston
