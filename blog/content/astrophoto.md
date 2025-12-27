---
title: "My Astrophotography Experience"
date: 2023-05-24
draft: false
tags: ["astrophotography", "photography", "hobby"]
---

Recently I've discovered the new hobby of astrophotography, although I don't have a lot of the gear, I try to grab every opportunity to get a photo. Recently one of those opportunities came by, I rented a camera and the lens and went to the location. This post I'll go through the process of taking these types of photos and what mistakes I made. (this was a first time experience for me too).

Now, I myself am pretty new to this hobby, there are still heaps of things to explore here, also there is a whole lot of other equipment that I did not know about. This is an expensive hobby to get into, so it is my suggestion that you do decent amount of research and only then buy the necessary equipment. Also it is not always necessary that you need that specific piece of equipment to take a photo there are some alternatives.

Some places where I took help from are:

- [Astrobiscuit discord server](#)
- [Astrobackyard](https://astrobackyard.com)
- [Allyn Wallace's Video on this topic](https://www.youtube.com/watch?v=dJMZQgyP7Dc)

Now lets get into the nitty gritty.

## Startrail Photo

![Startrail Photo](https://images.unsplash.com/photo-1684154912158-e73fa72705d0?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA==&auto=format&fit=crop&w=2972&q=80)

### Details

This photo was taken over 30 minutes (approx.).

- Shutter speed: 20 seconds
- ISO: 2000
- F-stop: f/2.8
- Camera used: Sony a7iii (non modified)
- Lens used: Sigma 24-70mm f/2.8

### Capturing

- You will need a stable tripod to take this photo. Mount your camera on the tripod.
- Now set the focus to manual, and set the composition of your photo. Now using the digital zoom feature on your camera zoom into the brightest star in the frame. Adjust the manual focus ring till the star is a nice crisp circular point.
- Here you can do either of two things, take one big long exposure photo or take multiple photos over short span and stack them up later. I chose to do the second as the first method is too risky and the entire shot is ruined if a single person walks in.
- You will want to now calculate how long the shutter speed is going to be. Now to set the shutter speed for this shot we will use the following formula:

  **Shutter speed (sec.) = 500/focal length (mm)**

  ***NOTE:*** This formula is only applicable to full frame cameras, if you are using a crop sensor (APS-C) you will want to replace the 500 with 300.

- Go to your camera settings and find the intervalometer or you can use an external intervalometer. It will keep taking the photos, set the time between to 1-2 seconds, do not exceed 4 seconds or you will start to have gaps in the photo.
- Now make sure no one walks in the frame or the setup does not shake.

If your camera supports it you will want to save the photos in Uncompressed RAWs. It will take up more space but you will end up with much better end result.

That is all!

### Processing

At the end you should end up with a set of hundreds photos (depending on how long you want it).

Now we will open them in a post-processing software, I'm a FOSS supporter and can't afford adobe so my choice will be darktable.

- In darktable, import all the photos that are taken
- Go to any photo and make some minor changes according to your preference like increasing the shadows and or decreasing the lights and make sure to tick the lens correction section.
- Save this as a style in the lighttable section. Select all the photos and apply the style and export them to a new folder but in .tiff format.

Next we are going to stack these photos, the software we are going to use is called "starStaX" go and download it from their site. After installing open the app and:

- Drag and drop all the photos you want to stack in the left container.
- On the right side we will select gap filling as the method.
- In the top left you will see an option to start stacking. You will see it stack in live time.
- Once the stacking is completed, go to the threshold slider and adjust it till all the star streaks are highlighted.
- Now play around with the amount slider till you get the result you want.
- Export the photo and you are done!

Now if you want to you can take this photo back to darktable to make more edits and if you think the foreground of the photo is over exposed or there are some issues in it you can go into GIMP and follow these steps:

- Import both the photo as layers, now the photo you want the foreground of should be at the top.
- Use the free select tool and then select the foreground and then add a layer mask which will hide the sky from the layer resulting in the photo you want.

## Milky-way Nebula

### Capturing

This process very much remains the same as before but you will want something called a tracking mount which will turn the camera at the exact rate it needs to move to keep the nebula in same place. If you do not have a tracking mount check how the nebula moves and slightly adjust the position of the camera every 2-3 minutes.

The shutter speed should be calculated as per the formula we used above, and then reduce it a tiny bit as we do not want trails this time. Take your time and experiment beforehand and find the right ISO.

To be fair when I took the photo I did not know this, the photo you see above is through a stack of 3 photos I took, the longer and the more photos you take the better the result will be.

You will also need to capture flat and bias frames to stack these photos these help get a more contrasty image and get rid of any vignetting that you may have, again I personally did not do this as I did not know about this at the time I took the photos. Astrobackyard has a great tutorial on how to take flat frames.

Now that you have taken the photos we can move on to processing these.

### Processing

Now processing is going to be very different from how we generally do it for normal photos or the photo above. First you will want to install the application called Siril, It is a free and opensource application and also install the following scripts: Mono processing without DBF and Mono processing without DB.

You will also need GIMP.

Now all the photos you have taken should be in .raw format, take open those photos in GIMP and export them to tiff files as before. DO NOT USE DARKTABLE AND ADD ANY AMOUNT OF PROCESSING.

Now make a folder and follow this exact directory structure:

- darks
- lights
- flats
- biases

All of your photos you have taken will go in the lights folder, then if you have taken any flat frames they will go in the flats folder.

Now that you have everything installed open Siril:

- Press the home icon, select the directory we just made
- Now go to scripts and run the script mono processing without DBF (or if you have flats run without DB) it will stack your photos into a result\.fit file
- Come back to home screen press "open" and open the result .fit file, It will look black for the most part but this is where the real magic happens.
- First we will run the background extraction process, go to image processing → background extraction it will show up as squares in the image, set the mode to RBF and remove the squares which are on your subject.
- Press compute, it will give a preview of how the image will look, If you are satisfied with the result then move on or you can play around with the squares till you get what you need.
- Next Go to image processing → Histogram transformation, then in the popup box there should be an icon called auto transform, click on it and hit apply, this should bring out the colors and pop out the image you really want.
- Go to histogram transformation again and in the slider just below the histogram slide it to make adjustments according to your needs.
- Now go to image processing again and Remove green noise, this will remove any unnecessary green noise from our image. According to your image, experiment with the amount slider.
- Next and final step we will go to image processing → and then color saturation, play with the sliders until you reach your desired image.
- Open this file in GIMP if you want to do any more processing such as getting rid of artifacts or other things you can do them here. and then simply export the photo in your desired image format and you are done!

This is a very simple guide on how to capture and process these photos and the equipment used here is very standard as well. But if you do want to go deeper into this I would suggest reading and watching Astrobackyard's videos and if you need any help go to the Astrobiscuit Discord server!


Thank you for reading~!
