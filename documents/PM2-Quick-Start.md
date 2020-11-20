# PM2 - ADVANCED, PRODUCTION PROCESS MANAGER FOR NODE.JS

PM2 is a daemon process manager that will help you manage and keep your application online 24/7.

### Installation

Install the latest PM2 version with NPM or Yarn:

```
$ npm install pm2@latest -g
# or
$ yarn global add pm2
```

### Start an app

The simplest way to start and monitor your application is by using this command line:

```
$ pm2 start app.js
```

Or start any other application easily:

```
$ pm2 start bashscript.sh
$ pm2 start python-app.py --watch
$ pm2 start binary-file -- --port 1520
```

### Managing processes

Managing application state is simple here are the commands:

```
$ pm2 restart app_name
$ pm2 reload app_name
$ pm2 stop app_name
$ pm2 delete app_name
```

Instead of `app_name` you can pass:

- `all` to act on all processes
- `id` to act on a specific process id

### Check status, logs, metrics

Now that you have started this application, you can check its status, logs, metrics and even get the online dashboard with [pm2.io](https://pm2.io/).

### List managed applications

List the status of all application managed by PM2:

```
$ pm2 [list|ls|status]
```

### Display logs

To display logs in realtime:

```
$ pm2 logs
```

To dig in older logs:

```
$ pm2 logs --lines 200
```
