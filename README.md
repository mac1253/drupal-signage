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

3. the terminal will ask you if you would ike to download them, press y, and hit enter. Do this until all required modules have been installed. Do this for the remaining modules

4. Install slick views
```bash
$ drush slick_views
```
#4. Configuring the site

Now we will configure the website to become a slide show

1. Go to your site in your browser, the URL should look something like this 
```bash
localhost/yoursite
```

2. Sign into an admin account and click Extend in the admin bar.
3. Scroll down and make sure Blazy, Blazy ui, Slick, Slick ui and Slick views have are checked. 
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

#### Lets add a content type to display

1. In your admin bar click Structure, and in Structure click Content Types
2. Delete the two current content types.
   click the little arrow next the Manage Fields button and click delete in the dropdown
   in the confirmation, click the delete button
   


 
