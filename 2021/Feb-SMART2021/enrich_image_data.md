# Using AI to enrich image data
This practical lab introduces the participants to the affordances of Google Cloud Vision API in research and Memespector-GUI.  [Memespector-GUI](https://github.com/jason-chao/memespector-gui/) is a tool with a graphical user interface (GUI) which helps researchers use Google Vision API.

# Contents
1. [Introduction to Google Vision API](#introduction-to-google-vision-api)
2. [Signing up for Google Cloud](#signing-up-for-google-cloud)
3. [Obtaining a credential file](#obtaining-a-credential-file)
   - [Create a project](#create-a-project)
   - [Enable Vision API](#enable-vision-api)
   - [Create a service account](#create-a-service-account)
4. [Downloading Memespector-GUI](#downloading-memespector-gui)
5. [Opening Memespector-GUI for the first time](#opening-memespector-gui-for-the-first-time)
   - [On Mac](#on-mac)
   - [On Windows](#on-windows)
6. [Using Memespector-GUI](#using-memespector-gui)
   - [Select the credential key file](#select-the-credential-key-file)
   - [Select the features to be detected](#select-the-features-to-be-detected)
   - [Add images to Memespector-GUI](#add-images-to-memespector-gui)
     - [Images on a computer](#images-on-a-computer)
     - [Images on the web](#images-on-the-web)
   - [Edit the names for output files](#edit-the-names-for-output-files)
   - [Invoke the API](#invoke-the-api)

## Introduction to Google Vision API
Google Vision API extract information from images using pre-trained artificial intelligence models.   It detects faces, emotions, text and explicit content, and suggests labels and similar images on the web.  See [here](https://cloud.google.com/vision/docs/features-list) for a full list of features.  The easiest way to try out Google Vision API is to use Google’s [drag-and-drop demo](https://cloud.google.com/vision/docs/drag-and-drop).

![Screenshot](enrich_image_data/drag-and-drop-try-it.jpg)

Just drop an image file from your computer into the designated area to see what Google Vision API can tell you about the image.  

![Screenshot](enrich_image_data/drag-and-drop-try-it-result.jpg)

The drag-and-drop demo is good enough if you only have a few images at hand to process.  In research, you may need to process hundreds or even thousands of images.   When you need to analyse images in batch, you should sign up for Google Cloud and use a suitable API client.

## Signing up for Google Cloud
If you have signed up for Google Cloud already, please jump to [Obtaining a credential key file](#obtaining-a-credential-key-file). 

Log on to [Google Cloud Platform](https://console.cloud.google.com) using your Gmail account.  Click `Activate` on the top right corner or `TRY FOR FREE` in the centre.

![Screenshot](enrich_image_data/gcp-activate.jpg)

Choose your country and check the box to agree to the service terms.  Click `CONTINUE`.

![Screenshot](enrich_image_data/gcp-signup-step1.jpg)

Complete the form with your name, address and details of your payment card.  

![Screenshot](enrich_image_data/gcp-signup-step2.1.jpg)

You must provide Google with a valid debit / credit card.  Otherwise, you will not be able to use Google Vision API.  From my experience, Google will check if your card is valid but will not charge on your card when you sign up.

Click `START MY FREE TRIAL` when you are done.

![Screenshot](enrich_image_data/gcp-signup-step2.2.jpg)

## Obtaining a credential file

After signing up for Google Cloud, you need to [create a project](#create-a-project), [enable Vision API](#enable-vision-api) and [create a service account](#create-a-service-account) before you can use Google Vision API.

### Create a project

Click `Select a project` on the top.  Then Click `NEW PROJECT`.

![Screenshot](enrich_image_data/gcp-project-new.jpg)

Give a name to the project.  Click `CREATE`.

![Screenshot](enrich_image_data/gcp-project-naming.jpg)

### Enable Vision API

Click the sandwich menu button on the top left.  Navigate to `API & Services` -> `Library`.  

![Screenshot](enrich_image_data/gcp-enableapi-navigate.jpg)

Click `Cloud Vision API`

![Screenshot](enrich_image_data/gcp-enableapi-select.jpg)

If you are unable to find `Cloud Vision API` for some reason, please type `vision` into the search box.  You should be able to see it now.  Click `Cloud Vision API`.

![Screenshot](enrich_image_data/gcp-enableapi-search.jpg)

Click `Enable`

![Screenshot](enrich_image_data/gcp-enableapi-enable.jpg)

### Create a service account

Click the sandwich menu button on the top left.  Navigate to `IAM & Admin` -> `Service Accounts`.  

![Screenshot](enrich_image_data/gcp-credential-navigate.jpg)

Click `CREATE SERVICE ACCOUNT`.

![Screenshot](enrich_image_data/gcp-credential-create.jpg)

Give a name to the account.  It is usually a name for your computer as service accounts are usually issued to computers.  Click `CREATE`.

![Screenshot](enrich_image_data/gcp-credential-naming.jpg)

Click `Select a role`

![Screenshot](enrich_image_data/gcp-credential-role1.jpg)

Navigate to `Basic` -> `Owner`.  

![Screenshot](enrich_image_data/gcp-credential-role2.jpg)

Click `CONTINUE`.

![Screenshot](enrich_image_data/gcp-credential-role3.jpg)

Leave these fields blank.  Click `DONE`.

![Screenshot](enrich_image_data/gcp-credential-done.jpg)

Under `Actions` on the right-hand side, click the sandwich button on the row of the service account you created just now.  Click `Create key`.

![Screenshot](enrich_image_data/gcp-credential-createkey.jpg)

Select `JSON` for `Key type`.  Click `CREATE`.

![Screenshot](enrich_image_data/gcp-credential-createjson.jpg)

Your browser should automatically download a .json file or ask you to save a .json file.  This is the `Google Cloud credential file` that Memespector-GUI will need.  Please move the credential file to a safe location after downloading.

![Screenshot](enrich_image_data/gcp-credential-downloadjson.jpg)

## Downloading Memespector-GUI

Visit [here](https://github.com/jason-chao/memespector-gui/releases/tag/0.0.1beta) to download Memesecptor-GUI.  Under `Assets`, choose the zip file that corresponds to the operating system on your computer.  

For Windows, please choose the win64 version by default.  Choose the win32 version if the win64 version does not work or you are sure that your Windows is 32-bit which is usually found on older computers.

![Screenshot](enrich_image_data/download-assets.jpg)

## Opening Memespector-GUI for the first time

When you open Memespector-GUI for the first time on Windows or Mac, the operating system may decline to run Memespector-GUI because of tightened security measures.  You have to take some extra steps to ask Windows or Mac to allow Memespector-GUI to run on your computer.

Usually, you will only need to take these extra steps once.  Next time, Memespector-GUI should run without further hindrance. 

### On Windows

After extracting the zip file, you will see the file `Memespector-GUI.exe` with an eye's icon. (Note: The file extension .exe may be hidden depending on the settings.)  Double click on it to open Memespector-GUI.

![Screenshot](enrich_image_data/firstrun-windows-exe.jpg)

If you see a window telling you not to run the app, click `More info`.

![Screenshot](enrich_image_data/firstrun-windows-moreinfo.jpg)

You will see that a new button will appear at the bottom.  Click `Run anyway`.  Then, Memespector-GUI should open in a few seconds.

![Screenshot](enrich_image_data/firstrun-windows-runanyway.jpg)


### On Mac

Safari may have extracted the zip file automatically for you after downloading it.  Open the `Memespector-GUI-macOS` folder and click `Memespector-GUI` inside.

![Screenshot](enrich_image_data/firstrun-mac-exe.jpg)

If you see a window asking that are you sure you want to open Memespector-GUI, click `Open`.  Then, Memespector-GUI should open in a few seconds.

![Screenshot](enrich_image_data/firstrun-mac-openrelease.jpg)

However, in some cases, you may not see the window above but instead encounter another window without an Open button.  In this case, see the additional steps as follows.

In case you see a window telling you that Memespector-GUI cannot be opened, click `Ok`.

![Screenshot](enrich_image_data/firstrun-mac-cannotrun.jpg)

Open [System Preferences](https://support.apple.com/guide/macbook-pro/system-preferences-apda966cb8af/mac) on your Mac.  Click `Security & Privacy`.

![Screenshot](enrich_image_data/firstrun-mac-systempreference.jpg)

Navigate to the `General` tab.  You should be able to see `"Memespector-GUI" was blocked from use because it is not from an identified developer` at the bottom of the tab.  Click `Open Anyway` to the right of that message.

![Screenshot](enrich_image_data/firstrun-mac-securitygeneral.jpg)

Click `Open`.

![Screenshot](enrich_image_data/firstrun-mac-openanyway.jpg)

## Using Memespector-GUI

*Note:  The graphical user interfaces of Memespsector-GUI are nearly identical across the Windows, Mac and Linux versions.  For illustrative purpose, the screenshots of the Windows version are used in this document.  The following steps also apply to the Mac and Linux versions of Memespector-GUI.*

![Screenshot](enrich_image_data/memespector-win.jpg)

### Select the credential key file

Click `Browse` to the right of the field for `Google Cloud credential file`.

![Screenshot](enrich_image_data/memespector-win-credentialfilefield.jpg)

Select the .json file you downloaded at the end of [creating a service account](#create-a-service-account).

![Screenshot](enrich_image_data/memespector-win-selectcredentialfile.jpg)

### Select the features to be detected

Check the features that you want Google Vision API to detect in the images.

![Screenshot](enrich_image_data/memespector-win-features.jpg)

- [Safety](https://cloud.google.com/vision/docs/detecting-safe-search) - adult, violent and racist elements
- [Face](https://cloud.google.com/vision/docs/detecting-faces) - emotional expressions of faces
- [Label](https://cloud.google.com/vision/docs/labels) - generalised labels defined by Google
- [Web](https://cloud.google.com/vision/docs/detecting-web) - web entities (inferred descriptions from similar images on the web), similar images, full/partial matching images, visually similar images and web pages with matching images
- [Text](https://cloud.google.com/vision/docs/ocr) - the text recognised
- [Landmark](https://cloud.google.com/vision/docs/detecting-landmarks) - well-known or prominent sites
- [Logo](https://cloud.google.com/vision/docs/detecting-logos) - logos of popular products

### Add images to Memespector-GUI

![Screenshot](enrich_image_data/memespector-win-addimages.jpg)

#### Images on a computer

Click `files on this computer`.  Select the image files.  Click `Open`.  The locations of the image files will be added to the `Image locations` box.

![Screenshot](enrich_image_data/memespector-win-individual-files.jpg)

![Screenshot](enrich_image_data/memespector-win-individual-file-locations.jpg)

If you want to add all images inside a folder with many sub-folders which also contain images, click `a folder on this computer`.  Select the folder.  The locations of all image files inside the folder and its sub-folders will be added to the `Image locations` box.

![Screenshot](enrich_image_data/memespector-win-a-folder.jpg)

![Screenshot](enrich_image_data/memespector-win-a-folder-locations.jpg)


#### Images on the web

Copy and paste the URLs of the images into the `Image locations` box.  Put one URL per line.

![Screenshot](enrich_image_data/memespector-win-web-locations.jpg)

### Edit the names for output files

Memespector generates two output files.  The JSON file stores the structured data values in full generated by Google Vision API.  The CSV file contains a version of the data transformed into a tabular format which may be easily opened using general software tools.

Click `Browser` to the right of each field to change the name and location of an output file.

![Screenshot](enrich_image_data/memespector-win-outputfiles.jpg)

### Invoke the API

Click `Invoke Google Cloud Vision API` after you have selected your `Google Cloud credential file`, added image files or URLs to the `Image locations` box and/or edited the output filenames.

![Screenshot](enrich_image_data/memespector-win-invoke.jpg)

Memespector-GUI will show the progress of sending the images to the Google Vision API.

![Screenshot](enrich_image_data/memespector-win-progress.jpg)

Once all images are processed, a message about the completion will be shown.  Open the output files to see the results.

![Screenshot](enrich_image_data/memespector-win-invoke-completion.jpg)
