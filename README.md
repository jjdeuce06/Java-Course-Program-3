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

### Initialization
The program initializes several key objects and variables:

### GridBag Objects:

A GridBagConstraints object named c is instantiated.
A GridBagLayout object named displ is created.
Arrays:
  colWeight: {1, 3, 1}
  rowWeight: {1, 1, 1, 1}
  colWidth: {1}
  rowHeights: {1, 2, 2, 3}
  
Configuration:
  displ.rowHeights is set to the rowHeights array.
  displ.columnWidths is set to the colWidth array.
  displ.columnWeights is set to the colWeight array.
  displ.rowWeights is set to the rowWeight array.

  
GridBagConstraints Settings:
  anchor: GridBagConstraints.WEST
  weightx, weighty, gridwidth, gridheight: All set to 1.

  
Frame Settings:
  The frame title is set to the current directory.
  The frame size is initialized to 900x300.
  The program then proceeds to position and configure individual items initialized in the main class.


Functions
  void display(String name)
  This function is responsible for managing and displaying the directory structure. Here’s a detailed breakdown of its logic:

Initialization:

A String[] array named filenames is created with a size of 10.
Handling the Input Parameter:

If name is not null:
  Check if name equals "..":
  If true, the current directory (curDir) is updated to its parent directory.
  Otherwise:
    A File object f is created in the current directory using name.
    If f is a directory, update curDir to this directory.
  Otherwise, check flags (SourceBool and targetBool):
  If one flag is false:
    Update the source label's text to the current directory.
    Set SourceBool to true.
    Enable the target button.
  If both flags are true:
    Set the filename's text to name.
    Mark the outfile flag as true.
  When name is null:
    Set filenames to the list of files in curDir.
    Update the frame title to the current directory.

    
  Processing Files:
    If filenames is not null, iterate through the array:
    Create a new File object for each filename.
    If the file is a directory, retrieve its children using the list() method.
    Traverse through this list and add a + to any string that is a directory using isDirectory()

  End of function:
    remove all elements from the list
    If the curDir has a parent, add .. next to its name
    If filenames is not empty, traverse through filenames and add it to the list

#### actionPerformed function
Create a source Object that gets the current event source
If the source is equal to the Target:
  set the direction field's text to the current directory and make the TargetBool true
If the source is equal to the filename:
  create a string named Filename that gets the text from the FileName field
  set the curDir value to the value in originaldirectory
  display a null value
  reset all text fields, buttons, and flags
If the source is equal to the list
  set the String named item to value returned by the getSelectedItem() function
  set the Filename to the absolute path and the appropriate filename if the item is a file
If the item is a regular file
  set the Filename to the path of the file and the filename
Otherwise
  set the Filename field to onlt the path

### windowClosing
  remove listeners and dispose of frame
  
