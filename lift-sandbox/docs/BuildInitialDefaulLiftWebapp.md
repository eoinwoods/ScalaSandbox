# Build a basic Lift webapp and see it running locally

-------------------------
## 1. Basic project construction ready for Lift

 - a word of warning there is a whole world of versioning pain out there if you are not careful.  You need to make sure that the plugin you want to use is compatable with the version of SBT you are using.  When you have plugins that need different versions of plugins to need to have the checked on one set to the one that most developers will use all the time.
 - create an empty directory called the project you want
 - create a dir called project and in there create a file called build.properties
 - define the sbt version in there, note we are using version 0.11.2 as the lifty plugin version only works with this version

        sbt.version=0.11.2

 - create a file called plugins.sbt and in the add the following (empty line separated):

        resolvers += Resolver.url("sbt-plugin-releases", new URL("http://scalasbt.artifactoryonline.com/scalasbt/sbt-plugin-releases/"))(Resolver.ivyStylePatterns)

        addSbtPlugin("org.lifty" % "lifty" % "1.7.4")

 - now in the root of the project create a file called build.sbt and in there put the following (empty line separated):

        name := "Static Data GUI"

        version := "1.0"

        scalaVersion := "2.10.0"

 - to test that the build process is put together correctly you can start SBT in REPL form (run sbt in the root of the project) and the type lifty and tab.  If it starts to auto-complete you know you are all set up.  For some reason it does not show on the tasks listing.


-------------------------
## 2. Lifty navigation

 - all the below assumes you are in teh lift REPL
 - to do anything with lifty you need to 'learn' templates
 - lifty's initial set of templates can be learned with:

        > lifty learn lift https://raw.github.com/Lifty/lifty/master/lifty-recipe/lifty.json

 - to list out the available templates with:

        > lifty templates lift

 - you can un-learn/delete the lift template with:

        > lifty delete lift

 - you can then create a new project using:

        > lifty create lift project
        > reload

 - and then start/stop the project with

        > container:start 
        > container:stop

-------------------------
## 3.3 Create the basic web app project

 - from the REPL run

        > lifty create lift project

 - accept the default for the version of lift
 - give the base package, eg org.suggs.sandbox.web.staticdatagui
 - set the project name, eg static-data-gui
 - set the version of scala ... suggest accept defaults
 - accept defaults for the project
 - agree to the overrides of the build and plugin files we created earlier
 - you now have a generated the basic application
 - reload and start with

        > reload
        > container:start

 - navigate to [localhost:8080](http://localhost:8080) and then see the default application

-------------------