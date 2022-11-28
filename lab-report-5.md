# Lab Report 5

grade.sh
```
# Create your grading script here

set -e

FILENAME="ListExamples.java"
CPATH=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

rm -rf student-submission
git clone $1 student-submission

cd student-submission

if [[ -f $FILENAME ]]
then
  echo "Correct: path exists and is a file"
fi

if [[ -e $FILENAME ]]
then
  echo "Correct: File name is correct"
else
  echo "Error! cannot find this file"
exit
fi

cp ListExamples.java ../
cd ..

set +e


javac -cp $CPATH *.java
java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > Xiafile.txt

if [[ $? -eq 0 ]]
then 
    echo "Tests all passed!"
else
    echo "Test not passed!"
    grep "Tests run" Xiafile.txt 
fi

set -e
```

<img width="825" alt="Screen Shot 2022-11-27 at 10 55 59 PM" src="https://user-images.githubusercontent.com/88987127/204215393-26c8ce1c-504b-4575-80d6-3534d39a953a.png">

<img width="831" alt="Screen Shot 2022-11-27 at 10 56 30 PM" src="https://user-images.githubusercontent.com/88987127/204215419-6f8e04de-2c48-4b6b-80c0-12903eddf57b.png">

<img width="841" alt="Screen Shot 2022-11-27 at 10 59 39 PM" src="https://user-images.githubusercontent.com/88987127/204215443-455fbdc0-2275-4c67-91cc-5d756192efee.png">


Trace: I choose the second one, which is the one that is correct

---

<img width="692" alt="Screen Shot 2022-11-28 at 10 38 52 AM" src="https://user-images.githubusercontent.com/88987127/204355103-cbdfe75c-84a4-4fed-bd46-7827989846ed.png">


```
if [[ -f $FILENAME ]]
then
  echo "Correct: path exists and is a file"
fi
```

This condition was true in this example, because the path was correct and there was a correct file in it. if[[-f]] means if the file exists, take actions based on the returned response. Since the file does exist, so print "Correct: path exists and is a file" to tell user that the system found this file successfully.

```
if [[ -e $FILENAME ]]
then
  echo "Correct: File name is correct"
else
  echo "Error! cannot find this file"
exit
fi
```

This condition was true, because the file name was correct. -e returns true if the target exists. Doesn't matter if it's a file, pipe, special device. In this case, the file exists, so print" Correct: File name is correct".

```
else
  echo "Error! cannot find this file"
exit
```

This command does not run because it is in an if branch that doesn’t evaluate. The if statement was true, so it went to "then" statement. else statement was ignored.

```
if [[ $? -eq 0 ]]
then 
    echo "Tests all passed!"
else
    echo "Test not passed!"
    grep "Tests run" Xiafile.txt 
fi
```

This condition was true, because the last command ran successfully with an exit code of 0 which leads to the if-condition here being evaluated to true.
So the system prints "Tests all passes" to let user know.

```
else
    echo "Test not passed!"
    grep "Tests run" Xiafile.txt 
fi
```
This command was skipped because it is in an if branch that doesn’t evaluate. Once if statement is true, it won't go to else statement. So this one was ignored
