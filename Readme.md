# Introduction to AOSP
## What is AOSP?
  - AOSP stands for Android Open Source Project.
  - Linux Based.
  - Beatufil UI.
  - Open Sourve
  - Support by different SOC vendors
  - ![/home/wagdy/Desktop/Embedded_Android_Guide/1-Android/Images/image.png](Images/image.png)




  # AOSP architecture
  1. Hardware (can be raspery pi)
  2. Android Kernel (special type of linux kernel)
  3. Bionic  => it's a special type of *gilibc*
  4. (HAL) Hardware Abstraction Layer
  5. Android Runtime (ART) => it's used when we install an apk app
  6. Set of managers (Activity Manager, Package Manager, Window Manager, Telephony Manager, Location Manager, Notification Manager, etc)
     - we will control those managers using the Qt app
     - They are set of services !
  7. Application Framework , Which communicates with the services throught the *binder* we will talk about it later
  8. Applications. can be Java or QT or Kotlin
  - ![alt text](Images/image2.png)




  # Let's get started with Android
  ## Tools we will use : **Git** - **repo** - **manifest file**
   - **Git** : is a version control system
   - **repo** : is a tool that we will use to manage the different repositories that we will use to build the AOSP
      - repo tool will use the manifest file to know which repositories to use
      - We will explain this later
   - **manifest file** : is a file that contains the list of repositories that we will use to build the AOSP


## Repo tool
 **Every version of android has a manifest file**
   - So we use **Repo** tool to get all the manifest files and then we specify which version we want from the android source code, for ex **android 11**
   That means you get the **platform**/, **kernel**/, **device**/, and **hardware**/ directories, but only the versions relevant to Android 11.

   steps:

   ```bash
   repo init -u https://android.googlesource.com/platform/manifest 
   ```
   - This command will get the manifest file from the google source code

   then we will use the following command to get the android 11 source code

   ```bash  
   repo init -u https://android.googlesource.com/platform/manifest -b android-11.0.0_r40
   ```
   - This command will get the android 11 source code

   then we will use the following command to get the source code

   - Go to directory ( .repo/manifests ) and open the file **default.xml** 
   then change :
   ```xml
   clone-depth="1" 
   ```

   ```bash   
   repo sync -j4
   ```
   It will take some time to download the source code


   > after fetching the version you will find: 
   # Directory structre :

   ![alt text](Images/image3.png)





   # build process
   ## Understanding the build process 
   - Acumulative process: it's


   1. Go to build dir and source the variables
   ```bash
   source build/envsetup.sh
   # this will load varaibles like TARGET_PRODUCT, TARGET_BUILD_VARIANT, TARGET_BUILD_TYPE, etc
   ```
   > Note: In variable TARGET_PROCDUCT_VARIANT we can choose the type of the build we want to do, for example **userdebug** or **user** or **eng**

   2. We will configure the varaibles loaded manually or using the interactive menu **lunch**

   ```bash  
   lunch
   # it will open a tool to choose the device we will use
   ```
