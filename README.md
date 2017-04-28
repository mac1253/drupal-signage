# Drupal-Signage
a small website for using Drupal as signage

Continuing from the [clean installation of ubuntu]( https://github.com/mac1253/Clean-Install-Ubuntu-15-Guide) and then [setting up development environment]( https://github.com/mac1253/roll-your-own), respectively, this guide will show you how to set up a slide show on a Drupal site, tailor made for digital signage

**Steps**
1. [Install Ubuntu]( https://github.com/mac1253/Clean-Install-Ubuntu-15-Guide)
2. [Set up development environment]( https://github.com/mac1253/roll-your-own)
3. [Install Drupal Modules](#3)
4. [Configuring the site](#4)

## #1. Install Ubuntu

Follow this guide to perform a clean installation of Ubuntu  

https://github.com/mac1253/Clean-Install-Ubuntu-15-Guide

## #2. Set up development environment

Follow this guide to set up a development environment

https://github.com/mac1253/roll-your-own

## #3. Install Drupal Modules

Assuming you followed and installed everything correctly from the previous guides this step will show you how to install the necessary Drupal modules needed

Drupal modules are extended features that can be added to your website.

1. Open a terminal, and change to your website directory
```bash
$ cd sites/yoursite
```

2. Now using drush, install the following drupal modules
```bash
$ drush en slick
```
*Using drush en command you not only download it but enable the module as well drush dl just downloads and installs the module but does not enable it *

3. the terminal will ask you if you would ike to download them, press y, and hit enter. Do this until all required modules have been installed and enabled. Do this for the remaining modules

4. Install slick views
```bash
$ drush en slick_views
```

5. Install Field group
```bash
$ drush en field_group
```

5. Install Field States UI
```bash
$ drush en field_states_ui
```

#4. Configuring the site

Now we will configure the website to become a slide show

1. Go to your site in your browser, the URL should look something like this 
```bash
localhost/yoursite
```

2. Sign into an admin account and click Extend in the admin bar.
3. Scroll down and make sure Field Group, Field States UI, Blazy, Blazy ui, Slick, Slick ui and Slick Views are checked. 
  a. If they are not, click the check box next to their name, scroll down to the bottom of the page and click install

#### Now we must set up a slick optionset

1. on the admin bar, click configuration, and on that page under the media section click the slick link

2. At the top, in the list tab, click the blue +add slick optionset button.

3. in the label put SlideshowOpt (or something more relative to your project)

4. Make sure that only these settings are set (This is for a basic full screen slideshow)
 Skin = fullscreen
 Autoplay = checked
 Infinite = checked
 Use CSS = checked
 Use CSS Transforms = checked
 Wait for animate = checked
 Autoplay = 3000 (how long a slide stays on for in milliseconds)
 Speed = 500 (how long a slide transitions for in milliseconds)
 
 The rest of the settings can be left at default.
 
 5. Click save at the bottom of the page
 
#### Now lets add an image style for the slideshow

1. in your admin bar go to configuration, and under media click Image Styles

2. In the image styles page, click the blue +Add image style button

3. Give the style a name and click Create New Style button

4. In the select new effect drop down, select Scale

5. Click the Add button, next to the drop down.

For this guide, we are assuming all displays will be a resolution at higheest 1920x1080, if you have a monitors high, use 
those dimensions

6. In the width text box enter 1920 and in the height box enter 1080. Check the Allow upscaling box at your discretion

7. Click the add effect button

8. Then click the Update Style button


#### Lets add some Taxonomy terms

1. In your admin bar click Structure, and in Structure click Taxonomy

2. click the +Add Vocabulary button 

For this guide we are using Campuses and buildings.

3. Add a name in the name textbox, in this guide We'll use Campuses. Give a description if you'd like

3. Click the save button and you should be directed to a page where you can add terms.

4. Click the +Add terms button

5. Give the term a name, I gave it West Campus and click the Save button. Clicking save doesnt bring you back to the previous page, it allows you to enter another

6. Enter all the terms you need to add. I added an East, North and South Campus

7. in the bread crumbs Home>>Administration>>Structure>>Taxonomy>>Campuses 
 Click on taxonomy. repeat Steps 2 through 6 for Buildings
 I had 3 terms for buildings. None, Library, Cafe


#### Lets add a content type to display

1. In your admin bar click Structure, and in Structure click Content Types

2. Delete the two current content types.
   click the little arrow next the Manage Fields button and click delete in the dropdown
   in the confirmation, click the delete button

3. After delete those two types, click the +Add Content Types button

4. Give the Content type a name. Mine was slide

5. In Submission form settings, have the title required
   In publishing options, uncheck everything 
   and in Menu settings uncheck everything 
   
6. Delete the body filed type by clicking the arrow next to the edit button. Click delete again to confirm the deletion

7. Click the +Add Field button

8. In the add in new field dropdown select taxonomy term, then in the text give the field a name, this field will be called Slide Campus Ref. Click the Save and Continue button

9. Leave the first dropdown as the default value and change the allowed number of values to unlimited. click Save Field Settings

10. Now check off the required box and under Reference type and check off Campuses. Click the save settings button (If you created the taxonomy vocabulary correctly it should be there)

 Using similar steps abover (7 though 10) add these field names with these values:
###### Slide Image
1. Label: Slide Image
2. Field Type: Image
3. Upload Destination: checked
4. Default Image: leave default (blank)
5. Allowed Number of Values: 1
6. Required Field: checked
7. Allowed File Extensions: png, jpeg, jpg *You can use what ever extensions in your own project*
8. File directory: images *change this name at your discretion*
9. Maximum Image Resolution: blank
10. Minimum Image Resolution: 900x480 *For our guide this is minimum size they can have for an image*
11. Maximum Upload size: 2mb
12. Enable Alt field: checked
13. Alt Field Required: checked
###### Slide Date Start
1. Label: Slide Date Start
2. Field Type: Date
2. Date Type: Date Only
4. Allowed Number of Values: 1
5. Required Field: checked
###### Slide Date End
1. Label: Slide Date End
2. Field Type: Date
3. Date Type: Date Only
4. Allowed Number of Values: 1
5. Required Field: checked
###### Slide Building Ref
1. Label: Slide Building Ref
2. Field Type: Taxonomy Term
3. Type of Item to Reference: Taxonomy Term
4. Allowed Number of Values: unlimited
5. Required Field: checked
6. Vocabularies: Building[Checked]

#### Manage Form Display

1. After all that go back to the content type Slide, and then click Manage Form Display

2. In the widget column, hide the following fields: Authored by, Authored on, Promoted to Front page, Stickys at top of lists, URL alias

3. Change the following value in the widget column for these fields

 Slide Campus Ref = Check boxes/Radio buttons and
 Slide Building Ref = Check boxes/Radio buttons 

4. Click the save button 

5. Now click the +Add Group button at the top in same tab.

6. Select a Group Type of Tabs, give the label a name of Wrapper. Click the Save and Continue button

7. Change the Veritcal value in the direction drop down to Horizontal and click the Create Group button

8. Now create a Group Type of Tab with Label name of Image, click the Save and Continue button. Change Default State to open then click the Create Group button

9. Do step 8 3 more times with these label names, Campuses, Buildings, and Dates, respectively. Do not change the Default state for these groups to open.

10. Click save at the botton of the page.

11. Using the Directional icon next to the group names, click and drag the Wrapper Group right below Title.

*If you dont see the directional icons next to the group names, then on the right sight of the page there should be an option to Hide Row Heights, click that and the directional icons should be displayed*

12. Now do the same for the Image tab group but put it under the wrapper group and drag it slightly to the right.

13. Take the image field group, drag that below the image group, and then drag it slighly farther than the image tab group. 

14. Do steps 12 and 13 for the corresponding groups and field groups such as Campuses, Dates, and Buildings.

This will give you a nice display to input slides

#### Make a Test slide 
1. In the admin bar, click content and then click the +Add Content button.
2. Fill in the required information, click the little arrow next to Save and unpublish and click Save and Publish.

You see and use this in the next set of steps.

#### Creating the slide show view
Now we will create the Slide show view which output the images in the manner we want it.

1. In the admin bar click Structures then click Views.

2. Similar to how we deleted Content Types, Disable, NOT delete, all the views except: Content, Custom block library, Files, People, and Taxonomy Term. Some Views may be disabled, enable them, they are towards the bottom of the page.

3. At the top of the page, click the +Add New View button.

4. The View Name will be Slide Show. View settings will Show: [Content] of Type: [Slide] sorted by: [Newest first]. Then click the Save and Edit button

This is where Drupal will query and format your images for a slide show. We will also inlcude a slide show management view.
###### All the settings in this View have the option "For", make sure for each display it is "This page(Override)" instead of "All Displays".
###### Click the Save button often!!!!

5. In your new view click the +Add button next to the Master display tab. Click Page in the drop downn.

6. click the Display Name link and Change the Name to Slide Show Management. Change the title. change for All Displays to This Page(override) and the title an empty text box.

7. Make Sure the Format is a Table

8. Click the Add button in the fields section. In the search bar type Slide

9. CHeck off these fields: Slide Image, Slide Campus Ref, Slide Building Ref, Slide Date Start and Slide Date End.

Dont check off the delta fields.

10. The settings for the field window will show up. Make sure the For drop down is set to This Page(Override)

11. I will be renaming the labels, to Building, Image, Date, etc so the word slide is not before it.

12. Click Apply(This Display) at the end!

#### Settings for Fields
##### Slide Campus Ref
1. For: This Page(Override)
2. Label: Campus

##### Slide Building Ref
1. For: This Page(Override)
2. Label: Building

##### Slide Date Start
1. For: This Page(Override)
2. Label: Date Start
3. Date Format: Default Long Date

##### Slide Date End
1. For: This Page(Override)
2. Label: Date End
3. Date Format: Default Long Date

##### Slide Image
1. For: This Page(Override)
2. Label: Image
3. Image Style: Medium (220x220)
4. Link Image to: File


Now that you have those settings set up, click save. When the page reloads scroll down to the auto preview and you can see your a preview of what we display on a page!

1. Going back to the fields section, next to the Add button click the arrow and then click Rearrange.
2. Using the rearrange icon, put it in this order: Image, Title, Campus, Building, Start Date, End Date
3. Click Apply(This Display)
4. The Filter Criteria for this page at its default works.
5. In the Page Settings section, change the Path to slidemanagement. Click Apply.
6. In the Header section, click Add, then type unfiltered text, check it and apply. 
7. Add the code below to the Content part and click Apply(This Display)
```html
<div class="add-node">
 <a href="/node/add/slide">Add a new slide</a>
</div>
```
*This link does not work on the local site but it does work on a live site.*

1. Click the Add display button. Make it a page.
2. Change the Display Name to West Campus
3. In The Format Section click the Table, and change it to Slick Carousel. Click Apply(This Display)
4. If the Slick Format settings didnt open up, just click settings right next to it the Format name
5. In those settings change the Optionset Main dropdown to SlideShowOpt.
6. Then change the Skin Main dropdown to Fullscreen.
7. In fields section of Slick Carousel Settings, Change the Main Stage dropdown to Image
8. In the fields section of displays, click the Rearrange button
9. Remove everything except the Slide Image. Click the Apply button
10. In the Filter Criteria section, click the Add button. Type Slide into the search and check box the following:
11. 
