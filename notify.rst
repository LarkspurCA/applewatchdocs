First Watch Notification
==========================

By Michael Hahn, May 2015

The notification context stream is one of the core functions for the Apple Watch. It consists of a message about timely information, such as incoming messages or upcoming appointments. It can also display useful information about a task at hand, such as workout status or recipe preparation. The watch initially displays a summary of the notification in the Short Look format, then advances to a Long Look if the user continues to view the notification. The Long Look is a scrollable display that includes notification details and Action Buttons. This section explains how to create your first watch notification.

Create an iPhone App
---------------------

Apple Watch applications always start with an app on the Phone. For this procedure, create a new empty phone app in Xcode.

1. Open Xcode. The Welcome to Xcode window is displayed.

  .. figure:: images/welcome.png
    :scale: 50

2. Select **Create a new Xcode project**. The template choices are displayed.

  .. figure:: images/templates.png
    :scale: 50

3. Select **iOS** and **Application**, and then choose **Single View Application**. Click **Continue**. The target options window is displayed.

  .. figure:: images/options.png
    :scale: 50

4. Enter the project options for your project, and then click **Next**. As a minimum set the following values. The screen capture shows the values for the hello example app.

  - Product Name
  - Organization Name
  - Language
  
5. Choose a location in your file system for your project and click **Create**. Xcode opens to the **hello** target of the new project.


Add WatchKit Targets
------------------------

Apple implements a watch app as two new targets, a WatchKit Extender and a WatchKit App. You add these to an existing iPhone app using Xcode.

1. In Xcode, select **File** -> **New** -> **Target**. 

  .. figure:: images/watchkit.png
    :scale: 50

2. Select **Apple Watch** under **iOS**, choose **WatchKit**, and Click **Continue**. The target options window is displayed.

  .. figure:: images/options2.png
    :scale: 50

3. Accept the default options and click **Finish**.

4. If prompted to activate a theme, click **Activate**. Xcode opens to the Hello WatchKit App target.

Add Watch Code
----------------

The default watch app only displays the time, so this example adds a text field to hold the Hello message and a button to change the hello message.

1. In the Navigator, expand the hello WatchKit App folder and click the Interface.storyboard. Locate and select the **Interface** graphic. This is where you build the watch app UI.

  .. figure:: images/storyboard.png
    :scale: 50

2. From the Object Library, drag a Label and a Button to the watch face.

  .. figure:: images/watchface.png
    :scale: 50

3. Add an IBOutlet for the label to the interfaceController. Visually, display both the storyboard and interfaceController. Control -> click the label and drag to the InterfaceController code, positioning the cursor near the beginning until an Insert Outlet appears. Stop there and a dialog opens where you can set the connection as an outlet and enter the name. Xcode then adds an IBOutlet variable for the label to the code.

  .. code-block:: swift
  
    class InterfaceController: WKInterfaceController {

      @IBOutlet weak var label: WKInterfaceLabel!

4. Similarily, add an action to the button. In the case of an action however, when the dialog opens choose action as the connection type and enter the name of the method that implements the action. Xcode adds an IBAction method.

  .. code-block:: swift
  
    @IBAction func didClick() {
    }

5. Implement the didClick method. This simple example updates the label text with the hello message.

  .. code-block:: swift
  
    var clickNumber = 0

    @IBAction func didClick() {
        var myString = "Hello World " + String(clickNumber++)
        label.setText(myString)
    }
	
Verify Operation
-----------------

In Xcode, start the emulator and view the watch. If necessary, select Apple Watch as the External Display under the Hardware menu.  When you click the button the Hello World text is displayed in the label, followed by the number of times you clicked the button.

  .. figure:: images/helloworld.png
    :scale: 50

  