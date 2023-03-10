# Android_Lint_CI-CD_Debug_Question_Answer

**Q.1. Lint and its Usage in Android Studio ?**

  * 1.What exactly is lint?

  Lint is a code scanning tool supplied by Android Studio that identifies, suggests, and corrects incorrect or dangerous code in a project.
  
  We’ve all been using Lint since we first started using Android Studio because it comes standard with support for Lint in every project. 
  The Lint will notify you of any errors found in your code, along with some suggestions and a warning level. You may use the advice to make 
  changes to your code. Lint’s biggest feature is that you may utilize it any way you see fit. If you provide a certain type of error in your 
  project, the Lint will only display that sort of mistake. Lint is adaptable in nature. Android Studio automatically executes the inspection 
  process when you create your project, but you can also examine your code manually or from the command line using Lint.
  
  * 2.Lint removal may be broken down into three steps:

  1.Making a lint.xml file: 
     
  In the lint.xml file, you may modify the Lint checks. You can write the checks you want to include in this file and disregard the checks 
  you don’t want to include. For example, if you wish to check for unused variables but not for naming problems, you may do so in the lint.xml file. 
  Aside from that, you may manually configure the Lint checks. In the following section of this article, we will look at how to perform manual lint checks.
     
  2.Lint Inspection: 
     
  The next step is to choose the source files that will be subjected to the Lint inspection. It may be your project’s.java file, .kt file, 
  or any XML file.

  3.The Lint Remover: 
     
  Finally, the lint tool examines the source and lint.xml files for structural code issues and, if any, suggests 
  code changes. It is recommended that we apply the lint recommendation before releasing our program.
  
  * 3.When Should You Use Lint?

  If you wish to publish your app on the Play Store or any other app store, it must be error-free. You must conduct a great deal of manual 
  testing on your app for this purpose. 

  Lint will detect the issues and propose solutions if you check each and every file in your code for faults. Errors or warnings 
  can be of the following types:

  Variables that have not been utilized
  Unjustifiable exceptions
  Imports that aren’t needed for the project, and much more
  So, before you publish your app, use Lint to thoroughly check your code.
  
  * 4.Lint Configuration

  To utilize Lint or just run inspections in your project, add Lint inspection to the lint.xml file or manually pick the list of issues 
  to be configured by Lint in your project using Android Studio.
  
  Add the list of issues to be configured in the lint.xml file to define manual inspections in your app. If you create a new lint.xml file,
  place it in the root directory of your Android project.
  
  Here’s an example of a lint.xml file:

  <?xml version="1.0" encoding="UTF-8"?>
  <lint>
    <issue id="GeeksIconMissing" severity="error" />
    <issue id="OldDimens">
        <ignore path="res/layout/merger.xml" />
        <ignore path="res/layout-xlarge/merger.xml" />
    </issue>
    <issue id="HellOWorld">
        <ignore path="res/layout/main.xml" />
    </issue>
    <issue id="someText" severity="ignore" />
  </lint>
  
  * 5.Run inspections manually:

  To manually run configured lint and other IDE inspections, select Code > Inspect Code. The results of the inspection appear in the Inspection Results window.
  
  * 6.Run lint from the command line

  If you're using Android Studio or Gradle, use the Gradle wrapper to invoke the lint task for your project by entering one of the following 
  commands from the root directory of your project:
  
  gradlew lint

  
  

