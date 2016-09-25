**testSDLa**
--------

testing SDL on Android.

**Tools and Library Usage**

 - Android Studio v.2.2
 - SDL2 v.2.0.4
 - SDL2_image v.2.0.1
 - SDL2_ttf v.2.0.14

**Build**

 - unzip SDL, SDL_image, SDL_ttf
 - edit in directory android-project, file AndroidManifest.xml, default.properties, project.properties to match current Android SDK
 - use Android Studio to import project from SDL, directory android-project
 - set output directory and its will be project name
 - open File/Project Structure and edit Android SDK version
 - open file build.gradle (module) and add these lines below 'buildToolsVersion':
   sourceSets {
       main {
           jni.srcDirs = []
       }
   }
 - move SDL, SDL_image, SDL_ttf to new created project, target <project>/app/src/main/jni and rename, too
 - edit Application.mk, remove x86 from APP_ABI
 - edit Android.mk in jni/src:
   edit LOCAL_C_INCLUDES, add SDL_image and SDL_ttf
   edit LOCAL_SRC_FILES, change YourSourceHere.c to main.cxx
   edit LOCAL_SHARED_LIBRARIES, add SDL2_image and SDL2_ttf (beware it has SDL2_*)
 - edit Android_static.mk in jni/src:
   edit LOCAL_SRC_FILES, change YourSourceHere.c to main.cxx
 - add main.cxx (from SDL2-test)
   edit main.cxx, change files to assets
 - run ndk-build in jni directory, like this:
   ndk-build NDK_LIBS_OUT=../jniLibs
 - on Android Studio, edit SDLActivity.java, uncomment SDL2_image and SDL2_ttf
 - compile and run
 - that all :)

**Thank**

 - google.com - to search every time when you want to learn any new things
 - stackoverflow.com - good community
 - www.sitepoint.com/using-c-and-c-code-in-an-android-app-with-the-ndk/ - for building SDL on Android
 - www.dinomage.com/2013/01/howto-sdl-on-android/ - for building SDL_image and SDL_ttf on Android

--------
Taworn T.

My English is very poor, I'm not English native, sorry. T_T

