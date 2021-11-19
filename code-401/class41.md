# Intent Filters
## Allowing Other Apps to Start Your Activity
If your app can perform an action that might be useful from another app, your app should be prepared to respond to action requests by specifying the appropriate intent filter in your activity.
For example, if you build a social app that can share messages or photos with the user's friends, you should support the ACTION_SEND intent. Then, when users initiate a "share" action from another app, your app appears as an option in the chooser dialog (also known as the "disambiguation dialog"), as shown in figure 1.
![](https://developer.android.com/images/training/basics/intent-chooser.png)

To allow other apps to start your activity in this way, you need to add an <intent-filter> element in your manifest file for the corresponding <activity> element.
When your app is installed on a device, the system identifies your intent filters and adds the information to an internal catalog of intents supported by all installed apps. When an app calls startActivity() or startActivityForResult(), with an implicit intent, the system finds which activity (or activities) can respond to the intent.
### Add an Intent Filter
The system may send a given Intent to an activity if that activity has an intent filter fulfills the following criteria of the Intent object:

* Action
A string naming the action to perform. Usually one of the platform-defined values such as ACTION_SEND or ACTION_VIEW.
Specify this in your intent filter with the <action> element. The value you specify in this element must be the full string name for the action, instead of the API constant (see the examples below).

* Data
A description of the data associated with the intent.
Specify this in your intent filter with the <data> element. Using one or more attributes in this element, you can specify just the MIME type, just a URI prefix, just a URI scheme, or a combination of these and others that indicate the data type accepted.
* Category
Provides an additional way to characterize the activity handling the intent, usually related to the user gesture or location from which it's started. There are several different categories supported by the system, but most are rarely used. However, all implicit intents are defined with CATEGORY_DEFAULT by default.
Specify this in your intent filter with the <category> element.
In your intent filter, you can declare which criteria your activity accepts by declaring each of them with corresponding XML elements nested in the <intent-filter> element.

For example, here's an activity with an intent filter that handles the ACTION_SEND intent when the data type is either text or an image:
<activity android:name="ShareActivity">
    <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="text/plain"/>
        <data android:mimeType="image/*"/>
    </intent-filter>
</activity>
[MORE SOURCE](https://developer.android.com/training/basics/intents/filters)