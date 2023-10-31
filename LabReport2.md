## Part 1:
__StringServer.java code__
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    ArrayList<String> engine = new ArrayList<String> ();
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            if (engine.isEmpty()) {
                return "Engine is empty";
            } else {
                StringBuilder response = new StringBuilder();
                for (int i = 0; i < engine.size(); i++) {
                    response.append(String.format("%d: %s%n", i+1, engine.get(i)));
                }
                return response.toString();
            }
        } else if (url.getPath().contains("/add-message")) {
            String[] parameter = url.getQuery().split("=");
            engine.add(parameter[1]);
            return "String Added";
        }
        return "404 Not Found";
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

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/74e234aa-6722-4104-a110-a6fded032746)
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/baf47127-1340-4ab9-a8ed-928c9b9971fe)

Methods in code that are called: 'handleRequest' in StringServer.java, 'handle' in Server.java

The arguments used in handleRequest is the url. The arguments used in handle is 'exchange' of type final & from class HttpExchange. This is called to authenticate each incoming request.

'handleRequest' gets changed by the user's input in the url. In this screenshot, it is "meow".  'handle' does not get changed because 'handle' forms the return string and writes it on the browser, where nothing changes because 'handleRequest' handles (haha) the input before 'handle' has to process the input.

![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/b544433b-3309-4615-ad02-b5a944c90aa5)
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/ec630e09-f470-43ee-8723-c7a250779188)

Methods in code that are called: 'handleRequest' in StringServer.java, 'handle' in Server.java

The arguments used in handleRequest is the url. The arguments used in handle is 'exchange' of type final & from class HttpExchange. This is called to authenticate each incoming request.

'handleRequest' gets changed by the user's input in the url. In this screenshot it is "woof".  'handle' does not get changed because 'handle' forms the return string and writes it on the browser, where nothing changes because 'handleRequest' handles (haha) the input before 'handle' has to process the input.


## Part 2:
The path to the private key for your SSH key for logging into ieng6 (on your computer or on the home directory of the lab computer):
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/a6487adc-8d5b-48cb-881f-270d3db34faa)

The path to the public key for your SSH key for logging into ieng6 (within your account on ieng6):
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/0baddb56-cd46-4fa8-8a68-14afe7f74ab8)

A terminal interaction where you log into ieng6 with your course-specific account without being asked for a password:
![image](https://github.com/ayynny/cse15l-lab-reports/assets/61796361/00c53775-1137-4fde-89a7-85819d095d66)

## Part 3:
I didn't know that you could sign into your account & access your files onto a different computer through remote servers. I also learned it's much more simple to host servers and run your own code on it than I initally thought. Super cool stuff!!!
