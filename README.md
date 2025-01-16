# Java-Course-Program-3
This program was the introduction to the Window in Java and my first personal experience with dealing with a program that opened a window

# Program Outline
This program is meant to implement a GUI using AWT methods presented in the class. These methods include ActionEvents, ActionListeners, WindowEvents, WindowListeners, and Frames

The program can accept an initial path in the command line, and will go to the current directory if an invaild directory is entered.

Once started the program is meant to mimic the file explorer. This means the user can navigate through directories, files, and folders. The user can select a source file, which will be placed into the source label when in source mode. This will then activate the Target button, which places the current directory path into the target directory label. 

The program allows the user to continually select a target file, which is placed into the target file name when in target mode. The user is allowed to continuously select a target file, which will be placed into the target file name when in target mode or the user can directly type the file into the field.


Directories that contain other directories will have a + next to the directory name and all directories that have a parent will include the .. next to the name

Files will contain the name and extension.

The top title bar contains the name of the current directory

Pressing enter or selecting the OK button will copy the source to the target.

Program will only copy when all information is provided, messages will be displayed if information is missing


## Implementation

### Beginning of Program
Program starts by checking if the user entered any directory name into the command prompt. If they did, the directory is checked for existence and passed into the Main constructor. If the directory does not exist or is not valid, the program gets the current directory using the getAbsolutePath() method and passes this into the main constructor

### Main class
Multiple variables are initialized in order to build the frame, these include
  1. Label objects named, Source, filename, direction, and messageLabel
  2. Button objects named Target and OK
  3. A List object named list
  4. A TextField object named FileName
  5. Booleans named SourceBool, TargetBool, and OutFile (these are used as flags)
  6. File objects named curDir and originalDirectory

The main constructor then begins the setup for a GridBagLayout. First, the program prints the directory passed in from the beginning of the program and sets the curDir variable's value to this directory. The value of original Directory is set to curDir. Then, an array of File objects named filenames is initialized with the values of the directory.listFiles() function. All booleans declared previously are set to false

#### GridBag initialization
  The program initializes a GridBagConstraints object named c to a new instance of GridBagConstraints() and a GridBagLayout object named disl to a new GridBagLayout(). Then 4 arrays are declared
  1. colWeight with values of {1, 3, 1}
  2. rowWeight with values {1, 1, 1, 1}
  3. colWidth with the value of {1}
  4. rowWeight with values {1, 2, 2, 3}


