# Introduction to Flask

This repository contains the minimal code to start a
[Flask](https://flask.palletsprojects.com/en/stable/) application. You can use
this as a template for your project or as a tutorial for setup.

## Create a new virtual environment

You need a virtual environment to install Flask and its dependencies.

```sh
python -m venv .venv
```

The new virtual environment will be in the hidden `.venv` directory.

## Activate the virtual environment

Before installing Flask, activate the virtual environment you just created.

```sh
source .venv/bin/activate
```

When you are done, you can run `deactivate` to exit the virtual environment.

## Install Flask

With the virtual environment activated, install the `flask` package directly or
use the `requirements.txt` in this repository.

```sh
pip install -r requirements.txt
```

Check that the dependencies are installed by running the `flask` command line
tool.

```sh
flask --version
```

## Run the application

Use `flask` to run the application in `app.py`.

```sh
flask run --debug
```

This command detects `app.py` in the current directory and uses it to load your
application. `flask` will only auto-load applications if they are in `app.py` or
`wsgi.py`. If your app is in a different file, use the `--app` option to specify
it. For more details, see
[Application Discovery](https://flask.palletsprojects.com/en/stable/cli/#application-discovery).

Let's look at some output from the command.

```
* Debug mode: on
```

This means your application is running in debug mode. Debug mode adds extra
features to help during development.

```
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
```

This message reminds you to use `flask` only for development. There are better
and safer ways to run your app in production.

```
* Running on http://127.0.0.1:5000
Press CTRL+C to quit
```

`flask` starts an HTTP server that listens for requests and uses your app to
handle them. The server keeps running until you stop it. To stop the server,
type `CTRL+C` in the terminal where `flask` is running.

```
* Restarting with stat
```

You don't need to restart the server every time you change your code. `flask`
detects file changes and reloads your app automatically. This is enabled by the
`--debug` option.

```
* Debugger is active!
* Debugger PIN: 173-179-167
```

Debug mode also enables the debugger. The debugger adds two useful features.

First, if your app raises an exception, the debugger shows a web page with a
formatted stack trace and the error location.

Second, from that page, you can open an interactive terminal to inspect
variables or run code in your server. Because this lets anyone run code on your
server, it is protected by a PIN. A new PIN is generated each time the app
starts.

> [!NOTE]
> This project has a special endpoint to test debug mode:
> http://127.0.0.1:5000/fail. Try running your app with and without the
> `--debug` option to see the difference.

## Update the application

Check [the code](app.py) and follow the comments!
