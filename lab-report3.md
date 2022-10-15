# Lab Report 3

## First one is Merge in ListExample.java

The failure-inducing input

<img width="823" alt="Screen Shot 2022-10-14 at 10 04 16 PM" src="https://user-images.githubusercontent.com/88987127/195969786-85c800f4-ac92-4659-802e-977377930c11.png">

The symptom (the failing test output)

<img width="862" alt="Screen Shot 2022-10-14 at 10 22 19 PM" src="https://user-images.githubusercontent.com/88987127/195970377-3891413a-c263-4e09-a232-f72171175527.png">

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
