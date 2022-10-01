# CSE15L Tutorial

VScode is a very powerful code editor that includes a terminal. We will use the terminal in this lab. So the first thing we have to do is install VScode.
Please go to this page to download and install [VScode]([http://a.com](https://code.visualstudio.com/))

**Here is VScode**
<img width="1021" alt="Screen Shot 2022-09-29 at 10 18 17 AM" src="https://user-images.githubusercontent.com/88987127/193385754-e30d2eb0-6b50-4991-ade8-44672598caab.png">

Once you downloaded the VScode, press"control" and "~" together. (The shortcut keys for mac and windows may be different)

Let us start learning to use the terminal to operate the computer remotely:


---

“ssh” is a keyword for remote access to a computer.
Add the username  after "ssh". For example, this is my username
```
ssh cs15lfa22@ieng6.ucsd.edu
```
And then enter your password, you will see this.

<img width="765" alt="Screen Shot 2022-09-30 at 2 43 35 PM" src="https://user-images.githubusercontent.com/88987127/193386121-d8b3f85e-0a51-405d-acd3-a11c4e1d95c8.png">


**Congratulations! you have successfully accessed the server remotely. If you are unable to log in with your password, remember to ask your professor for help during office hours. He will help you with magic.**

```
Here are some specific useful commands to try:

cd ~
cd
ls -lat
ls -a
ls <directory> where <directory> is /home/linux/ieng6/cs15lfa22/cs15lfa22abc, where the abc is one of the other group members’ username
cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/
cat /home/linux/ieng6/cs15lfa22/public/hello.txt
```
Here is a example output:

<img width="975" alt="Screen Shot 2022-09-30 at 4 17 37 PM" src="https://user-images.githubusercontent.com/88987127/193386211-15c2c7cf-06d6-4566-84aa-45a695e93a02.png">

scp is a way to safely copy files to another computer 

Assume you have a file like this:
```
public class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
You can use `javac WhereAmI.java` and `java WhereAmI` to compile and run this code

Now we use this command to copy paste
```
scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/

```

Once you have done that, you will see this if you press "ls"

<img width="869" alt="Screen Shot 2022-09-30 at 4 39 31 PM" src="https://user-images.githubusercontent.com/88987127/193386611-540dd319-fb47-4eeb-9a29-b4187dc6339c.png">

These codes allow you to see information such as the current operating system. When you see information such as Linux, it proves that the information of the server is now displayed.

## Do you feel like typing your password makes you impatient? Especially when the password is wrong? It's time to throw out your password!

**Use this keyword on your computer( DO NOT LOG IN YOUR ACCOUNT)**

```
ssh-keygen
```
You will see this:

<img width="896" alt="Screen Shot 2022-09-30 at 7 30 23 PM" src="https://user-images.githubusercontent.com/88987127/193388681-61e67f69-e408-494c-9c11-d39a0f560688.png">


Copy and paste this line

```
/Users/hongyuan/.ssh/id_rsa.pub
```

Use this command to copy and paste the key to the server, so next time we don't have to enter password.

```
$ scp /Users/joe/.ssh/id_rsa.pub cs15lfa22@ieng6.ucsd.edu:~/.ssh/authorized_keys
# You use your username and the path you saw in the command above
```

**Congratulations! You will never need a password again!**

<img width="950" alt="Screen Shot 2022-09-30 at 7 51 43 PM" src="https://user-images.githubusercontent.com/88987127/193391355-6dcf5bd7-a25f-4505-95da-854f171debad.png">


> You are almost done! Now you can play with it, like remote running

```
$ ssh cs15lfa22@ieng6.ucsd.edu "ls"


$ cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI

```

This is my example

<img width="603" alt="Screen Shot 2022-09-30 at 8 07 50 PM" src="https://user-images.githubusercontent.com/88987127/193392154-56aa627f-90e5-4f3b-bd45-3d25c2cf44dd.png">

