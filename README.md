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
  
**Q.2. What is Baseline in Lint ?**

 If you are working on a large project and want to identify future mistakes that may arise while adding additional codes to your project, 
 you can set a baseline to your project and the lint will create the errors that happened after that baseline. As a result, lint will 
 disregard prior code problems and only alert you about new lines of code introduced after the baseline.

 To include a baseline in your project, add the following line to the build.gradle file:

 android {
   lintOptions {
     baseline file("lint-geeksforgeeks-example.xml")
   }
 }
 This will generate a lint-baseline.xml file, which will serve as a baseline for your project. To add another baseline, remove the file and lint once more.
 
**Q.3. What is lintOptions ?**

You can configure lint by adding a lintOptions section in the build.gradle file:

android {
   lintOptions {
         // set to true to turn off analysis progress reporting by lint
         quiet true
         // if true, stop the gradle build if errors are found
         abortOnError false
         // set to true to have all release builds run lint on issues with severity=fatal
         // and abort the build (controlled by abortOnError above) if fatal issues are found
         checkReleaseBuilds true
         // if true, only report errors
         ignoreWarnings true
         // if true, emit full/absolute paths to files with errors (true by default)
         //absolutePaths true
         // if true, check all issues, including those that are off by default
         checkAllWarnings true
         // if true, treat all warnings as errors
         warningsAsErrors true
         // turn off checking the given issue id's
         disable 'TypographyFractions','TypographyQuotes'
         // turn on the given issue id's
         enable 'RtlHardcoded','RtlCompat', 'RtlEnabled'
         // check *only* the given issue id's
         check 'NewApi', 'InlinedApi'
         // if true, don't include source code lines in the error output
         noLines true
         // if true, show all locations for an error, do not truncate lists, etc.
         showAll true
         // whether lint should include full issue explanations in the text error output
         explainIssues false
         // Fallback lint configuration (default severities, etc.)
         lintConfig file("default-lint.xml")
         // if true, generate a text report of issues (false by default)
         textReport true
         // location to write the output; can be a file or 'stdout' or 'stderr'
         //textOutput 'stdout'
         textOutput file("lint-results.txt")
         // if true, generate an XML report for use by for example Jenkins
         xmlReport true
         // file to write report to (if not specified, defaults to lint-results.xml)
         xmlOutput file("lint-report.xml")
         // if true, generate an HTML report (with issue explanations, sourcecode, etc)
         htmlReport true
         // optional path to report (default will be lint-results.html in the builddir)
         htmlOutput file("lint-report.html")
         // Set the severity of the given issues to fatal (which means they will be
         // checked during release builds (even if the lint target is not included)
         fatal 'NewApi', 'InlineApi'
         // Set the severity of the given issues to error
         error 'Wakelock', 'TextViewEdits'
         // Set the severity of the given issues to warning
         warning 'ResourceAsColor'
         // Set the severity of the given issues to ignore (same as disabling the check)
         ignore 'TypographyQuotes'
         // Set the severity of the given issues to informational
         informational 'StopShip'
         // Use (or create) a baseline file for issues that should not be reported
         baseline file("lint-baseline.xml")
         // Normally most lint checks are not run on test sources (except the checks
         // dedicated to looking for mistakes in unit or instrumentation tests, unless
         // ignoreTestSources is true). You can turn on normal lint checking in all
         // sources with the following flag, false by default:
         checkTestSources true
         // Like checkTestSources, but always skips analyzing tests -- meaning that it
         // also ignores checks that have explicitly asked to look at test sources, such
         // as the unused resource check.
         ignoreTestSources true
         // Normally lint will skip generated sources, but you can turn it on with this flag
         checkGeneratedSources true
         // Normally lint will analyze all dependencies along with each module; this ensures
         // that lint can correctly (for example) determine if a resource declared in a library
         // is unused; checking only the library in isolation would not be able to identify this
         // problem. However, this leads to quite a bit of extra computation; a library is
         // analyzed repeatedly, for each module that it is used in.
         checkDependencies false
    }
}
 
 

  
  

