# simple-python-web-server

This project is not fully tested may contain bugs.  Use at your own risk.  The main purpose of this project is to provide an example of a simple python web server and the usage of GET and POST for the same.  This is not intended for a production environment.  Please feel free to submit issues and/or PRs if you do encounter a bug or deprecated function.  Other issues or PRs that you feel would be beneficial to the spirit of this repository are also welcome.

[Simple python web server to demonstrate GET/POST handling](http://joelinoff.com/blog/?p=1658)

> Use it as a starting point to understand the package when creating your own custom web server for handling specific types of requests but recognize that it is not suitable for a production environment. To use it in such an environment you would, at the very least, want to add improve the error handling and add threading support. You would probably also want to add SSL/TLS support.


#### Running the Server

After you download the server, you simply run it by typing “./webserver.py” or “python2.7 ./webserver.py“. That will start the server on your local host using port 8080. If that port is already in use, then use the -p option to specify another port like this “./webserver.py -p 9000“. Do not try to use port 80. It will interfere with the normal operation of your system.

As the simple web server runs, it will print out informational messages as it is running to show you what is happening.

#### This is the list of options available from the server.

##### -d DIR, –daemonize DIR
Daemonize this process, store the 3 run files (.log, .err, .pid) in DIR (default “.”). Version 1.2 or later.

##### -h, –help
Help message.

##### -H host, –host host
The hostname (e.g. localhost).

##### -l LEVEL, –level LEVEL
Logging level: noset, debug, info, warning, error, critical. Version 1.2 or later.

##### –no-dirlist
Disable directory listings. Version 1.2 or later.

##### -p port, –port port
The port (e.g. 8080).

##### -r dir, –rootdir dir
The web files root directory.

##### -v, –verbosity
Increase verbosity. Not used.

##### -V, –version
Print the version number and exit.

### Accessing the Server

Now that the server is running you can access the webserver.html page by entering the following URL: http://127.0.0.1/webserver.html (you can also use 0.0.0.0 if that is easier to type). 

If you enter data in the “Form Using GET” fieldset, the argument values will appear in the webserver output log. If you enter data in the “Form Using POST” fieldset, the argument values will in the webserver output log and on a new page. In both case, you inspect the source code to see how the form data was captured and processed from the browser request.

Now try entering “http://127.0.0.1:8080/info” and you will see internal server information. This shows, in a crude way, how you can enter custom URLs.

At this point you have verified that the simple web server is working. If you want to go further, you try creating your own HTML or javascript files.

### Implementation Discussion

This implementation uses the BaseHTTPServer and cgi packages for creating the server and processing browser requests. It uses argparse to manage the command lines arguments. There are a number of interesting features of this example.

The first is the use of the class factory make_request_handler_class to allow the request object to have access to the command line options, specifically the root directory for accessing files to display for GET requests. You could add any arbitrary class arguments this way. For example you add the content headers for handling different file extensions which in the current implementation are in the do_GET() handler method.

Another interesting feature is setting the content type based on the file extension.

Yet another interesting feature is that the POST request handler redirects to a custom page with a back button. This is simply to demonstrate that it can be done.

Enjoy!
