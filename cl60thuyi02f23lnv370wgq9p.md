## Build a simple YouTube video downloader with python

If you have tried to download a YouTube video before,  then you know the frustration of going through a million ads, just to get a two megabyte file. In this article, we will create our own simple YouTube video downloader using python.

**Requirements**

Before we begin, you should have:
- python. If not, follow [this](https://www.python.org/downloads/) guide to install it. 
- a code editor
- Pytube 
- Tkinter

Pytube is a lightweight Python library for downloading youtube videos.
Tkinter is a  standard GUI( Graphical user interface) library for python.

To install Pytube and Tkinter, run the following commands on CLI(command line interface) using pip installer.
```
pip install tk
Pip install pytube
``` 

If you are using python 2.x, install Tkinter as Tkinter(notice the uppercase T).

```
pip install Tkinter
``` 
We will follow the following steps in building a YouTube downloader:
1. Import required libraries
2. Create display window
3. Create link entry
4. Create download function


**Step 1: Import required libraries**

We need to import the modules that we installed.

```
from tkinter import * # import all libraries from tkinter module
from pytube import YouTube # import YouTube library from pytube module

``` 
**Step 2: Create a display window**


```
root = Tk() # initializes tkinter to create display window
root.geometry('400x250') # width and height of the window
root.resizable(0, 0) # sets fix size of window
root.title(' our awesome youtube downloader') # gives the window a title

Label(root,text = 'Youtube Video Downloader', font ='arial 20 bold').pack()
# The rest of the code 

root.mainloop() # executes when we want to run the program
``` 

- **Label()** widget above displays texts that users cannot modify.
- **root** is the name of the window.

When we run the code above, it gives us a blank window. The remaining code will go in between the Tk() and mainloop(). The resulting window is as below:

![Screenshot from 2022-07-25 12-38-08.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1658754045980/-tg7R-LJq.png align="left")

**Step 3: Create link entry**

The next step is to create an entry where we can paste a YouTube link.

```
var = StringVar() # specifies variable type
Label(root, text = 'Paste Link Here:', font = 'arial 15 bold').place(x= 100 , y = 60)


label = Message( root, textvariable = var, relief = RAISED )
link_enter = Entry(root, width = 70,textvariable = var).place(x = 32, y = 90)

var.set('Paste Link Here:')
``` 

- **var** stores the URL entered as string.
- **Entry()** widget is used when we want to create a text field.
- ** textvariable **is used to obtain the current text variable's value for the entry widget.
- **place()** is used to position the widget at a certain location.

The output of the above code is as shown in the picture below:


![Screenshot from 2022-07-25 16-04-17.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1658754420662/sb9UowDIT.png align="left")

**Step 4: Create download function**

 Now that we have our window up and running, we need to create a function to download the videos.
We also need a button that when clicked, will call this function. 
```
def Downloader():
    url =YouTube(str(var.get())) # gets youtube link from link entered and converts it to string
    video = url.streams.first() # video is downloaded in the first stream the video is in
    video.download() # initializes the download
    Label(root, text = 'DOWNLOADED', font = 'arial 15').place(x= 180 , y = 210) # shows "DOWNLOADED" when the download is complete
Button(root,text = 'DOWNLOAD', font = 'arial 15 bold' ,bg = 'red', padx = 2, command = Downloader).place(x=180 ,y = 150) 
``` 


The function *Downloader* above takes a YouTube URL entered, looks for the first stream (360p, 720p,1080p e.t.c) and downloads the video. 
The final output is:

![Screenshot from 2022-07-25 16-19-12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1658755167748/var15gpk4.png align="left")
After pasting the URL as below, hit the *DOWNLOAD* button. Wait a few seconds, and you should have your video downloaded.

![Screenshot from 2022-07-25 16-56-11.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1658757451278/5S6mg6jin.png align="left")

**Conclusion**
 
We have successfully developed a youtube video downloader using python. I hope this has been helpful.
Thanks for reading.



 

