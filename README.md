# ViewBindingAndroidJava
ViewBinding in Android (Implemented using Java)

Add the "buildTypes" tag into the build.gradle(app) to enable the view binding

<pre>
    <code>
        
android {
    compileSdk 32

    defaultConfig {
        applicationId "com.example.viewbindingandroid"
        minSdk 30
        targetSdk 31
        versionCode 1
        versionName "1.0"

        testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
    }


    //Enabling ViewBinding
    viewBinding{
        enabled = true
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
}
    </code>
</pre>


Create a variable outside onCreate method- (variable name will be suggested by Android studio itself once we type "Activity" with "Binding" as suffix)

<pre>
  <code>
ActivityMainBinding mainXml;
 </code>
</pre> 

After enabling the ViewBinding update this line in your Java file  inside onCreate() method
# OLD
<pre>
  <code>
       setContentView(R.layout.activity_main);
  </code>
</pre> 

# NEW
<pre>
  <code>
        mainXml = ActivityMainBinding.inflate(getLayoutInflater());
        setContentView(mainXml.getRoot());
  </code>
</pre> 

Now we dont need to create a variable ie. TextView, EditText or Button...
we can simply access the UI element using the Binding variable : 

<pre>
  <code>
    mainXml.txt1.setText("This is page two : ");
    // binding_var_name.id_of_view.method_We_want_to_access.
 </code>
</pre> 

       

## View Binding
>  Normally we change something in java textview then same changes will reflect in XML code
>  Before we change a textView value in java code we need to reference it using findviwebyid(R.id...)
>  If we have many TextView then referencing would be difficult so we use ViewBinding #problem1 resolved
>  when we have multiples XML files then some component id would be same ie for some button xml1 has same id as xml2
> every activity will have its own binding class

activity_main.XML <-> mainActivityBindingClass(Java) <-> ActivityMain.java

![Screenshot 2022-08-11 at 11 39 12 PM](https://user-images.githubusercontent.com/68295105/184209325-0afdc8cc-3e2a-4f1a-b643-2fb4ea548f5c.png)



