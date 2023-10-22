__Part 1:__
##  StringServer.java code
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
