# *Image annotation app for UWTV surveys*

*This R Shiny application was built to annotate HD-stills from UWTV surveys carried out by the Marine Institute.*


## Dependencies

The app has only been tested in Windows 10 and 7. For better performance of the app we suggest to run it on Google Chrome.  


It was built using R (Version 3.5.2), RStudio (Version 1.1.463) and the following R libraries:  
"colorspace", "DT", "exifr", "hms", "jpeg", "magick", "plotrix", "raster", "shiny", "shinyBS", "shinyFiles", "shinyjs", "shinythemes", "shinyWidgets"


Two additional software were used to ensure correct extraction of exif information from the images:

* ActivePerl (Version 5.26). https://www.activestate.com/products/activeperl/
* ExifTool (Version 11.26). https://sno.phy.queensu.ca/~phil/exiftool/index.html




## Set up

The app requires an specific folder structure around to read the images (input), and to write .csv and .txt files with the data generated by the app (output):

### Parent folder
Set up in the code by...  
"volumes_parent <- c(Home = "C:/Parent_folder", getVolumes()())""


### Inside the parent folder we need three subfodlers:

#### Subfolder for the app
* No need to set up in the code.  
* Example: C:/Parent_folder/subfolder_with_the_app  
* Inside this subfolder we will have the app.R script with all the code.

#### Subfolder for the images:
* Set up in the code by...  
"volumes <- c(Home = "C:/Parent_folder/reduced_stn", getVolumes()())""
* Inside this subfolder we will have one subsubfolder for each station carried out during the survey, for example: C:/Parent_folder/reduced_stn/stn_122
* Inside each station's subsubfolder we will have another folder called "reduced_images", for example: C:/Parent_folder/reduced_stn/stn_122/reduced_images
* Inside this last folder we will have all the .jpg files for the station.

##### Format of the images:
To ensure proper functioning of the app, the images must be:
* .jpg files
* Maximum size of 135 kB
* Dimmensions of 1229 x 691 pixels (for 22-27 inches monitors)


#### Subfolder for the outputs:
* No need to set up in the code.  
* Specific name: C:/Parent_folder/app_outcome  
* Inside this subfolder we will have three subsubfolders for different outputs:  
* C:/Parent_folder/app_outcome/ancillary  
* C:/Parent_folder/app_outcome/non_countable_time  
* C:/Parent_folder/app_outcome/counts  
Inside the subsubfolder for the counts we will have a .csv file called "SURVEYS_and_COUNTERS.csv" with three columns: "survey", "counter" and "VideoOperatorID". This .csv file must be filled out by the SIC.  


## app GUI

Once the app is running, the user should follow these steps:
* Select a Survey ID
* Select a Counter ID
* Select a Station ID
* Press "load" button
* Check if number of images is correct
* Press an arrow on the keyboard
* Images should start displaying on the GUI
* Footage viewer instructions:
  * Up arrow: Pause
  * Rigth arrow: Play
  * Left arrow: Rewind
  * Timer on the under the image shows current time along the station (starts on 00:00, should finish on 10:00 for 10 minute stations)
  * Speed selector next to the timer to amke the 'video' slower
  * Non-countable time: use 'start', 'stop', and 'confirm' buttons to log in non-countable time (i.e. sand cloud covering the image) -> app_outcome/non_countable_time
  * Ancillary data: fill all the radio buttons on the top-right and press 'Save ancillary data to .csv' to do so -> app_outcome/ancillary
  * Annotation of footage:
    * Pause the footage and click on the burrow you want to annotate. A blue circle will appear where you clicked, and a new row will be added on the table to the right of the image.
    * To delete annotations: select the row you want to delete on the table. Press 'Delete all burrows in current image' button
    * This table will update live a .csv file called surveyID_stationID_counterID_counts.csv inside app_outcome/counts




## Patches and pull requests

Your patches are welcome. Here's the suggested workflow:
 
* Fork the project.
* Make your feature addition or bug fix.
* Send a pull request with a description of your work.


## Author
Mikel Aristegui  
Fisheries Ecosystems Advisory Services,  
Marine Institute / Foras na Mara,  
Ireland


## License
Released under the [GNU AGPLv3 license] https://github.com/IrishMarineInstitute/nephrops-burrow-counting-app/blob/master/LICENSE.md