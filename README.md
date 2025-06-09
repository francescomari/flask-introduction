# Introduction to Flask

This repository contains the minimal amount of code to bootstrap a
[Flask](https://flask.palletsprojects.com/en/stable/) application. You can use
this repository as a template for your project, or as a tutorial for setting up
a new project.

## Create a new virtual environment

You need a virtual environment to install Flask and its dependencies.

```sh
python -m venv .venv
```

The new virtual environment will be in the (hidden) directory `.venv`.

## Activate the virtual environment

Before installing Flask, you need to activate the virtual environment you just
created.

```sh
source .venv/bin/activate
```

When you are done with this project, you can run the `deactivate` command to
deactivate the virtual environment.

## Install Flask

With the virtual environment activated, you can install the `flask` package
directly, or rely on the `requirements.txt` committed in this repository.

```sh
pip install -r requirements.txt
```

Verify that the dependencies are correctly installed by running the `flask`
command line tool.

```sh
flask --version
```

## Run the application

You use `flask` to run the application defined in `app.py`.

```sh
flask run --debug
```

This command detects that a file called `app.py` is in the current working
directory, and will use that file to load and run your application. `flask` will
only automatically load applications if they are defined in files called
`app.py` or `wsgi.py`. If your application is in a file with a different name,
you will need to use the `--app` option to specify which application to load.
For further details about how to run an application, look at [Application
Discovery](https://flask.palletsprojects.com/en/stable/cli/#application-discovery).

Let's look at some of the output of the command.

```
* Debug mode: on
```

This message tells you that your application is running with "debug mode"
active. As you will see below, this mode adds some extra features to your
application that will help during development.

```
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
```

This message makes very clear that you are supposed to use `flask` only during
development, because there are much better and safer ways to run your
application in production. `flask` is useful only for development.

```
* Running on http://127.0.0.1:5000
Press CTRL+C to quit
```

`flask` starts an HTTP server that continuously listens for requests, and uses
your application to decide how those requests should be handled. HTTP servers
are long-running programs: they are always up and running, waiting for clients
to connect and send requests, until they are explicitly stopped. To stop the
HTTP server started by `flask`, you have to type `CTRL+C` in the same terminal
window where `flask` is running.

```
* Restarting with stat
```

This message tells you that you don't need to restart the HTTP server every time
you change your code or some other file in your project. Instead, `flask` will
detect that some files have changed, and will automatically reload your
application. This feature is added by the `--debug` option.

```
* Debugger is active!
* Debugger PIN: 173-179-167
```

Another feature added by `flask` in debug mode is the debugger. The debugger
adds two very useful features to your application. 

First, if your application raises an exception, the debugger will print a web
page that nicely formats the stack trace and shows where the exception
originated from. 

Second, from the same page you can open an interactive terminal running within
your running application to inspect variables or run arbitrary code in your
server. Because this feature allows anybody seeing that page to run arbitrary
code in your server, and therefore in your computer, the feature is protected by
a PIN. The first time the application starts, a new PIN is generated.

> [!NOTE]
> The application in this project has a special endpoint that you can use to
> test the debug mode: http://127.0.0.1:5000/fail. Try to run your application
> with and without the `--debug` option and see how the behavior changes.

## Update the application

Head over to [the code](app.py) and follow the comments!
