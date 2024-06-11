# AppliedStatsInteractive
 
This is an R package which deploys interactive notebooks to accompany an introductory course in applied statistics. The notebooks follow the freely available [OpenIntro Statistics (4Ed)](http://www.openintro.org/os) textbook and supplementary resources, and are now in beta as a supported supplement [at OpenIntro.org](https://www.openintro.org/book/os/). 

You can install this package by running the following command in R (which requires the `devtools` package as a prereqisite): `remotes::install_github("agmath/AppliedStatsInteractive")`. You may also need to run `remotes::install_github("rundel/learnrhash")` in order to install Colin Rundel's `{learnrhash}` package which is also required for using these notebooks, but isn't always installed automatically. You can also simply *use* the tutorials by creating a free [Posit.cloud](https://posit.cloud/) account and copying [this workspace](https://posit.cloud/content/6328402) with the notebooks and required packages pre-loaded. Copying the Posit.cloud workspace is the way I have my students access these notebooks in my own classes. Once logged in, click on the `Tutorial` tab in the top-right pane of RStudio and then click the `Start Tutorial` button next to the notebook you'd like to run.

## Branches Available

Because of the changes I've made over the last several years, I've decided to leave several branches of the `{AppliedStatsInteractive}` package available for installation. I'll eventually rename the `old` branch to something more descriptive.

+ `main`: This branch will undergo continued development. It makes heavy use of the pipe operator (`%>%`) and `{tidyverse}`-aligned syntax. It also includes robust, guided-hint infrastructure for interactive code cell questions.

  + Install with: `remotes::install_github("agmath/AppliedStatsInteractive")`
+ `old`: This branch does not inlcude the use of the pipe operator (`%>%`) and uses very little `{tidyverse}` syntax.

  + Install with: `remotes::install_github("agmath/AppliedStatsInteractive@old")`
+ `nohints`: This banch is not yet available, but it will include the notebooks on from the `main` branch but will suppress the hints so that they are unavailable to learners. 

  + Install with: This branch not yet available

## Most-Recent Updates

**Hint Infrastructure Added:** I've gone through all of the interactive notebooks and added significant hint infrastructure to code block questions. The hints are meant to guide the learner, as if they were being prompted by an instructor. I imagine that some instructors will prefer that their students not see the hints, so I'll create a separate branch on this repository which sets the notebooks to hide hints from users. I'll include an update to the **Available Branches** section above once the hint-free notebooks are available.

**Conversion to `inference()` from `{statsr}`:** The original versions of the notebooks used a custom `inference()` function that was loaded when `atheism.RData` and when `nc.RData` were loaded. I've switched the notebooks so that they now utilize the more common version of `inference()` from the `{statsr}` package. This change impacts the Topic 13 and Topic 17 notebooks.

**Greater leaning into the `{tidyverse}`:** I've removed all (I think) occurrences of the dollar sign ($) for column selection in favor of syntax that is more aligned with the `{tidyverse}`. While this approach is often more verbose, I find it much more readable and intuitive for students at the introductory level.

**Notebook Grading Update/Resources:** I've developed a few resources useful for grading students on these notebooks. You should be able to copy all of the files to your own Google Drive and use them for your classes. There are three files in this [Google Drive Folder](https://drive.google.com/drive/folders/1zj2yvJyRFgXmwaqWGkUkbIRXTwj3Jpip?usp=sharing), described as follows:

+ `Hash Code Submission Form` -- a Google Form for collecting student hash codes generated at the end of each notebook. 
+ `Hash Code Submission Form (Responses)` -- a Google Sheet collecting responses from the form above.
+ `grading_script.r` -- an R Script to automatically consume student hash codes from the Google Sheet above and build an `overall_grades` data frame, containing one row per student and calculated grades using weightings supplied by the user. Lines 5 - 29 provide instructions for using the grading script.

I've finally renamed the folers and files so that the topic notebooks appear in the appropriate order within the Tutorials pane.

I've set the notebooks to allow skipping of questions. This should prevent the notebooks from forcing you to execute every code cell before moving from one section to the next.

I've edited the instructions associated with generating the hash code for submission at the end of each notebook. These instructions are now more flexible -- suggesting that students "generate the hash code *if* their instructor is requesting they do so". Additionally, I've removed the institution-specific link which directs students to Southern New Hampshire University's BrightSpace instance.

**Significant Change:** As of April 4, 2022 I've begun updating the notebooks to discuss use of the pipe (`%>%`) operator and more `dplyr` functionality. For example, the most recent update suggests using `diamonds %>% summarize(avg_carat_wt = mean(carat))` rather than `mean(diamonds$carat)` to compute the mean of the `carat` column from the `diamonds` data frame. While this requires a bit more typing, it results in more flexible code and greater readability. 

Prior to pushing these updates, I created a branch in this repository labeled *old*. If you prefer the notebooks as they were, without making use of (or mentioning) the pipe operator, you can install the package from that branch. You'll do so by running `remotes::install_github("agmath/AppliedStatsInteractive@old")`


## Grading Functionality

I've updated the package to include functionality from Colin Rundel's `learnrhash` package. This allows students to generate a hash code, which encodes their completed notebook -- students can then paste this hash code into a web-form (such as Google Forms) and then the instructor can reproduce and assess the student's work using `learnrhash` and the student's hash code. See more about this functionality from the [`learnrhash` repo](https://github.com/rundel/learnrhash). Some users will need to install `learnrhash` manually in order for the notebooks to run -- you can do this with `remotes::install_github("rundel/learnrhash")`. I am working on a fix for this issue.

## Running Tutorials

Once the package has been installed you can run the individual notebooks by navigating to the `Tutorials` tab in RStudio's top-right pane. You'll just need to click the *Start Tutorial?* button to render and work through the corresponding interactive notebook. If you get an error stating that `learnrhash` must be installed, you can install it manually using `remotes::install_github("rundel/learnrhash")` -- once `learnrhash` is installed, hit the *StartTutorial?* buttton again. If you prefer to run the tutorials from a web browser rather than RStudio's Tutorials pane, you can access the tutorials using commands of the following structure: `learnr::run_tutorial(NOTEBOOK_NAME, package = "AppliedStatsInteractive")`

The available notebooks are as follows:
+ 0_StartHere
+ 1_IntroToData
+ 2_IntroToR
+ 3_DescriptiveNumCat
+ 4_DataViz
+ 5_DiscreteDistributions
+ 6_NormalDistribution
+ 7_DiscreteDistributionsLab
+ 8_NormalDistributionLab
+ 9_FoundationsForInference
+ 10_IntroInferenceLab
+ 11_HTandCIprop
+ 12_InferencePractice
+ 13_InferenceCategoricalLab
+ 14_ChiSquare
+ 15_HTandCInum
+ 16_InferencePractice
+ 17_InferenceNumericalLab
+ 18_ANOVA
+ 19_LinearRegression

The notebook named 4_DataViz is an adaptation of the data visualization chapter from Hadley Wickham and Garrett Grolemund's [R for Data Science](https://r4ds.had.co.nz/).

## A Note on Rendering Workbooks

(**Note:** *This is a non-issue if running workbooks from the tutorials pane*). Multiple calls to `learnr::run_tutorial()` in a single R session cause rendering errors in the notebooks -- exercises are not rendered correctly. This can be avoided by either restarting R `Ctrl+Shift+F10` or by closing RStudio and re-opening before rendering a second workbook. If you already attempted to render the notebook and experiences the rendering error, you should use your file manager to navigate to the folder containing the workbook and delete the associated *html* file. You can identify the location of the files on your machine by running `find.package("AppliedStatsInteractive")`. Calling `learnr::run_tutorial()` now will re-build the html file. I will update this section when a better workaround is discovered.
