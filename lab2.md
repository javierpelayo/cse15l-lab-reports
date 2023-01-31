## Lab 2 - String Web Server, Bugs and Reflection

## Part 1

```java
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> strList = new ArrayList<>();

    public String handleRequest(URI url) {
        String s = new String();

        if (url.getPath().equals("/")) {
            for (int i=1; i < strList.size(); i++) {
                s += strList.get(i);
            }
            s += url.getPath();
            return s;
        } else {

            if (url.getPath().contains("/add-messages")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    strList.add("\n" + parameters[1]);

                    for (int i = 0; i < strList.size(); i++) {
                        s += strList.get(i);
                    }

                    s += "\n" + url.getPath();
                }

                return s;
            }

	    }

        return "404 Not Found!";
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
![Image]()

![Image]()


When the main method in StringServer is called, we call `Server.start()` to start up the web server, in Server we create an HttpServer object called "server" which calls a `create()` method to make a socket address using the port provided. 

Then it proceeds to create a request entrypoint using the created HttpServer object using the following statement:

`server.createContext()`

We then proceed to actually start the server process by the following:

`server.start()`

Where `start()` is a method defined in HttpsServer

Once we make a request to the server by visiting the url associated with it the following method is called:

`public String handleRequest(URI url)`

where the url we visited is passed down to it.

Specifically looking into this method we can see that url.getPath() returns the decoded portion of the path url which is essentially everything in the url after the domain name and before the query.

So this would return a string with either just "/" or "/add-messages"

The relevant arguments would essentially be the URI object itself which contains the methods needed to essentially split the whole url into the essential portions using either the `getPath()` method or the `getQuery()` method.

The values changed in this class would essentially be at the point where the query is split into its two components, specifically e.g. "s=hello" where using the `url.getQuery().split("=") gives us a String array of size two that has the following elements:

["s", "hello"]

The first element would always be the same since it is our parameter which we are checking for new strings.

The second element would change if we were to specify something different.

In essence our URI objects gets changed since the query would be different, but so would the String array used when splitting it.

We also have our instance variable "strList" that would be changed by the addition of new strings as well as the "String s" variable we are using to store the added strings to return back to the HttpServer and be rendered on the page.

## Part 2

## Part 3








































































