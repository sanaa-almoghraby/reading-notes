# Tasks and the back stack 
A task is a collection of activities that users interact with when trying to do something in your app. These activities are arranged in a stack—the back stack—in the order in which each activity is opened.
# Lifecycle of a task and its back stack
![](https://developer.android.com/images/fundamentals/diagram_backstack.png)
# Back press behavior for root launcher activities
Root launcher activities are activities that declare an Intent filter with both ACTION_MAIN and CATEGORY_LAUNCHER. These activities are unique because they act as entry points into your app from the app launcher and are used to start a task.

* System behavior on Android 11 and lower
The system finishes the activity.
* System behavior on Android 12 and higher 
# Background and foreground tasks
![](https://developer.android.com/images/fundamentals/diagram_multitasking.png)

# Multiple activity instances
# Multi-window environments

In this regard, these are the principal <activity> attributes that you can use:

* taskAffinity
* launchMode
* allowTaskReparenting
* clearTaskOnLaunch
* alwaysRetainTaskState
* finishOnTaskLaunch
And these are the principal intent flags that you can use:

* FLAG_ACTIVITY_NEW_TASK
* FLAG_ACTIVITY_CLEAR_TOP
* FLAG_ACTIVITY_SINGLE_TOP

# Defining launch modes
Launch modes allow you to define how a new instance of an activity is associated with the current task. 
* Using the manifest file

* Using Intent flags
==============================================
# Save key-value data 
If you have a relatively small collection of key-values that you'd like to save, you should use the SharedPreferences APIs. A SharedPreferences object points to a file containing key-value pairs and provides simple methods to read and write them. Each SharedPreferences file is managed by the framework and can be private or shared.

# Get a handle to shared preferences
* getSharedPreferences() — Use this if you need multiple shared preference files identified by name, which you specify with the first parameter. You can call this from any Context in your app.
* getPreferences() — Use this from an Activity if you need to use only one shared preference file for the activity. Because this retrieves a default shared preference file that belongs to the activity, you don't need to supply a name.

# Write to shared preferences
To write to a shared preferences file, create a SharedPreferences.Editor by calling edit() on your SharedPreferences.

Pass the keys and values you want to write with methods such as putInt() and putString().

