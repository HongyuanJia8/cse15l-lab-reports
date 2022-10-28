# Lab Report 3


## Part 1
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
import java.util.*;

class Handler implements URLHandler {
    int num = 0;
    public String handleRequest(URI url){
        // System.out.println(url)
        ArrayList<String> items = new ArrayList<String>();
        if (url.getPath().equals("/"))
        {
            return String.format("List: %d", items);

        }
        else if(url.getPath().equals("/add"))
        {
            String[] parameters = url.getQuery().split("=");
            if(parameters.length >= 2 && parameters[0].equals("s"))
            {
                items.add(parameters[1]);
                return String.format("%s added", parameters[1]);
            }

            
        }
        else if(url.getPath().equals("/search"))
        {
            String[] parameters = url.getQuery().split("=");
            if(parameters.length >= 2 && parameters[0].equals("s"))
            {
                ArrayList<String> output = new ArrayList<String>();
                for (String s : items)
                {
                    if(s.contains(parameters[1]))
                    {
                        output.add(s);
                    }
                }
                return String.format("%s", output.toString());
            }
        }
        return "404 not found"; // 404
    }
}

class SearchEngine{
    public static void main(String[] args) throws IOException
    {
        if(args.length == 0)
        {
            System.out.println("The number should between 1024 and 49151");
            return;
        }

        int p = Integer.parseInt(args[0]);

        Server.start(p, new Handler());
    }
}
```


## First one is Merge in ListExample.java

The failure-inducing input

<img width="823" alt="Screen Shot 2022-10-14 at 10 04 16 PM" src="https://user-images.githubusercontent.com/88987127/195969786-85c800f4-ac92-4659-802e-977377930c11.png">

The symptom (the failing test output)

<img width="1039" alt="Screen Shot 2022-10-28 at 3 30 26 PM" src="https://user-images.githubusercontent.com/88987127/198745551-eda9f1cb-731e-48af-8a5f-bb85feee7dd9.png">


The bug (the code fix needed)

<img width="865" alt="Screen Shot 2022-10-14 at 10 26 21 PM" src="https://user-images.githubusercontent.com/88987127/195970470-5c0e5064-a952-4b19-b8e3-7b19e9ff6b7a.png">

Then, explain the connection between the symptom and the bug. Why does the bug cause that particular symptom for that particular input?

In line 46, it was index1 += 1, but the condition is index2 < list2.size(), so the index1 always += 1 and never stop, this is a infinite loop.

## Second one is Merge in ListExample.java

The failure-inducing input

<img width="796" alt="Screen Shot 2022-10-14 at 10 41 20 PM" src="https://user-images.githubusercontent.com/88987127/195971148-09ee2c08-a4ec-40c1-9646-fb26962112e8.png">

The symptom (the failing test output)

<img width="796" alt="Screen Shot 2022-10-14 at 10 41 20 PM" src="https://user-images.githubusercontent.com/88987127/195971159-4f2efe81-ff1b-4613-88a5-f887956071cf.png">

The bug (the code fix needed)

<img width="868" alt="Screen Shot 2022-10-14 at 10 42 26 PM" src="https://user-images.githubusercontent.com/88987127/195971182-699a7e52-8adc-49ef-8bb1-95b067388620.png">

Then, explain the connection between the symptom and the bug. Why does the bug cause that particular symptom for that particular input?

it should be "newArray[i] = arr[arr.length - i - 1];" and "return newArray;"
it always changed the originial input, change it to 0. Becase newArray is empty.
