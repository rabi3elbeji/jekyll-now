---
layout: post
title:  Introduction to NDK for Android mobile apps
date:   2019-08-22 00:00:00
categories: [Artificial Intelligence]
tags: [Artificial Intelligence]
published: true
comments: true
---

<center><img src="/images/post5/ndk-intro.png" alt="Introduction to NDK for mobile apps" style="max-width: 100%; height: auto;"/></center>

### Introduction

When you try to build a high-performance and optimized game or across platform application or maybe an application with advanced and complicated AI tasks in production, you most probably choose as programming language a low level one such as `C` or `C++` . But if the platform is a mobile device, such as Android, is it still the same case of using a native language?

Short answer: **Yes!**

In fact, Android apps can be categorized into two types:
  - `Dalvik applications` that include `Java` code and use the Android official SDK API **only** and necessary resource files, such as xml and png, compiled into an APK file.
  - `Android NDK applications` that include `Java` code and resource files as well as `C/C++` source code and sometimes assembly code. All native code is compiled into a dynamic linked library (`.so` file) and then called by Java in the main program using a JNI mechanism.

### What is the NDK and when should you use it?

The Android Native Development Kit (`NDK`) is a companion tool to the Android SDK. The NDK is a powerful tool for developing Android applications because it allow you to build  performance-critical portions of your applications in native code. When using Java code, the Java-based source code needs to be interpreted into machine language using a virtual machine. In contrast, the native code is compiled and optimized into binary directly before execution. With proper use of native code, you can build high performance code in your application, such as hardware video encoding and decoding, graphics processing, and arithmetical operation.

Also, the NDK Reuses legacy native code. C/C++ codes can be compiled into a dynamic library that can be called by Java code with a `JNI` mechanism. JNI is an abbreviation for Java Native Interface. It allows C++ and Java parts to talk to each other in the simplest terms. For example, if you want to call a function from C++ in Java, you should write a JNI interface for this purpose.

If you write native code, your applications are still packaged into an .apk file and they still run inside of a virtual machine on the device. The fundamental Android application model does not change.

<center><img src="/images/post5/ndk-use-cases.png" alt="Android NDK use cases" style="max-width: 100%; height: auto;"/></center>

### ABI: Application Binary Interface

As you know, Android is distributed for a variety of devices. Each device might have a different CPU architecture. When you develop an Android application that contains C++ code, you should care about the platforms on which your application will run. The C++ code should be compiled as a library for each platform you target. You can compile the library for all the supported platforms, or you can choose to compile it for only one platform.

You can list any subset of the ABIs the NDK supports, as shown below:

```gradle
android {
    defaultConfig {
        ndk {
            // Tells Gradle to build outputs for the following ABIs and package
            // them into your APK.
             abiFilters 'x86', 'x86_64', 'armeabi-v7a', 'arm64-v8a'
        }
    }
}
```

When this flag is not configured, Gradle builds and packages all available ABIs.

<center><img src="/images/post5/abi-cpus.png" alt="ARM and Intel Mobile CPUs architectures" style="max-width: 80%; height: auto; margin:2%;"/></center>

<center><img src="/images/post5/supported-abi.png" alt="ABIs and supported instruction sets" style="max-width: 60%; height: auto; margin:2%;"/></center>

To reduce the size of your APK, consider configuring multiple APKs based on ABI—instead of creating one large APK with all versions of your native libraries, Gradle creates a separate APK for each ABI you want to support and only packages the files each ABI needs.

> **Hello World project**

**1.** <b><u>Install the NDK, CMake, and LLDB</u></b>

Under `Configure` select `SDK Manager` then check the **LLDB**, **NDK**, and **CMake** checkboxes.

<center><img src="/images/post5/helloworld/step00.png" alt="Select SDK Manager" style="max-width: 50%; height: auto; margin:2%;"/></center>

<center><img src="/images/post5/helloworld/step0.png" alt="Install the NDK, CMake, and LLDB from the SDK Manager" style="max-width: 50%; height: auto; margin:2%;"/></center>


**2.** <b><u>Start a new Android Studio project</u></b>

Open Android Studio and click **Start a new Android Studio project**. This will initiate the new project wizard.

<center><img src="/images/post5/helloworld/step1.png" alt="Start a new Android Studio project" style="max-width: 50%; height: auto; margin:2%;"/></center>

**3.** <b><u>Select a Native C++ project</u></b>

<center><img src="/images/post5/helloworld/step2.png" alt="Select a Native C++ project" style="max-width: 50%; height: auto; margin:2%;"></center>

**4.** <b><u>Configure Your project</u></b>

Next, give your project an application name, company domain (important when deploying your app to the Play Store and also influences your Java code namespaces), project location, and package name.

<center><img src="/images/post5/helloworld/step3.png" alt="Configure Your project" style="max-width: 50%; height: auto; margin:2%;"/></center>

**5.**  <b><u>Customize C++ support</u></b>

Determining what C++ Standard to use or when to upgrade can be tricky. The idea here is to use the C++ Standard thats most compatible your libraries, dependencies and existing source code. For this tutorial we'll use the Toolchain Default. But future versions of your projects may use more modern C++...

<center><img src="/images/post5/helloworld/step4.png" alt="Configure Your project" style="max-width: 50%; height: auto; margin:2%;"/></center>

**6.**  <b><u>Project structure</u></b>

<center><img src="/images/post5/helloworld/step5.png" alt="Hello World app view" style="max-width: 50%; height: auto; margin:2%;"/></center>

- Native Code in **native-lib.cpp**

```cpp
#include <jni.h>
#include <string>

extern 'C' JNIEXPORT jstring JNICALL
Java_com_rabiielbeji_helloworld_MainActivity_stringFromJNI(
        JNIEnv *env,
        jobject /* this */) {
    std::string hello = "Hello Rabii from C++";
    return env->NewStringUTF(hello.c_str());
 }
```

- Cmake file

```
cmake_minimum_required(VERSION 3.4.1)

add_library( # Sets the name of the library.
        native-lib

        # Sets the library as a shared library.
        SHARED

        # Provides a relative path to your source file(s).
        native-lib.cpp)
```

- Main java activity class **MainActivity.java**

```java
// Used to load the 'native-lib' library on application startup.
static {
    System.loadLibrary("native-lib");
}

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    // Example of a call to a native method
    TextView tv = findViewById(R.id.sample_text);
    tv.setText(stringFromJNI());
}

/**
 * A native method that is implemented by the 'native-lib' native library,
 * which is packaged with this application.
 */
public native String stringFromJNI();
```

**7.**  <b><u>Result after running the app</u></b>

<center><img src="/images/post5/helloworld/step6.png" alt="Hello World app view" style="max-width: 30%; max-height: 30%;"/></center>

>
**CODE**
The code is available on [NDK_HelloWorld](https://github.com/rabi3elbeji/NDK_HelloWorld)


> **Image processing with OpenCV**

<b><u>What's OpenCV?</u></b>

OpenCV (Open Source Computer Vision) is a library of programming functions mainly aimed at real-time computer vision. In simple language it is library used for Image Processing. It is mainly used to do all the operation related to Images.

It has a C++ interface and support Android :smile:

Below is an example of some of the basic operations on the image.

<center>
<img src="/images/post5/opencv/rgb.jpg" alt="RGB original image" style="max-width: 30%; max-height: 30%; margin: 1%;"/>
<img src="/images/post5/opencv/gray.jpg" alt="Gray original image" style="max-width: 30%; max-height: 30%;margin: 1%;"/>
<img src="/images/post5/opencv/canny.jpg" alt="Vanny original image" style="max-width: 30%; max-height: 30%;margin: 1%;"/>
</center>

>
**CODE**
Clone [NDK OpenCV](https://github.com/rabi3elbeji/NDK_OpenCV) from github and follow usage steps

> **Image processing with OpenCV DNN**

OpenCV DNN (Deep Neural Networks) module has been released from OpenCV 3.3 version and it's designed for running multiple deep learning models trained from different deep learning frameworks like Caffe and TensorFlow. It supports various networks architectures based on YOLO, MobileNet-SSD, Inception-SSD, Faster-RCNN Inception,Faster-RCNN ResNet, and Mask-RCNN Inception.

### Conclusion

Using NDK in your applications allows them to achieve a high level of performance in terms of memory or processing time. But also, it's not recommended to use the NDK with ordinary applications that don't have a critical need for memory or speed performance, because Kotlin and Java are already optimized and simple to use and implement.

In future posts, I will cover more examples of using Computer Vision and Deep-Learning with NDK.

### References

1- [Android* Application Development and Optimization on the Intel® Atom™ Platform](https://software.intel.com/en-us/articles/android-application-development-and-optimization-on-the-intel-atom-platform)

2- [Android ABIs](https://developer.android.com/ndk/guides/abis)

3- [Droidcon SF 2018 - Getting Started with the Android NDK](https://www.youtube.com/watch?v=NT8blJ2-jeU&list=PLFTIxMvfPSS0WST-XWNhumx4V3-Cf47m0&index=2&t=0s)

4- [Getting Started with C++ and Android Native Activities](https://medium.com/androiddevelopers/getting-started-with-c-and-android-native-activities-2213b402ffff)

5- [Android NDK eng](https://github.com/cathybgyz/zimenglyu/blob/master/_posts/2018-11-27-tflite-android-ndk-eng.markdown)

6- [Opencv Native Androidstudio](https://github.com/leadrien/opencv_native_androidstudio)

7- [Deep Learning in OpenCV](https://github.com/opencv/opencv/wiki/Deep-Learning-in-OpenCV)
