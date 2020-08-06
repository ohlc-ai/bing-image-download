# Bing Images Download


[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)



# Introduction

This directory contains Bing image-scraping software forked from https://github.com/ultralytics/google-images-download, and updated by OHLC.AI, and **is freely available for redistribution under the MIT license**.

While this script runs perfectly on PyCharm & Terminal, our main goal is to run the script on Google Colab & saving all the images directly to Google drive. I will explain steps to use the script on Google Colab and saving images in Google Drive folder.

# Requirements

 - [Google Colab](https://colab.research.google.com/)
- Python 3.8 or later with all of the `pip install -r requirements.txt` packages including:
- `selenium`

# Install
Run this on Google colab line by line
```bash
!pwd
```
It should show output as **/content**. That's the directory you're currently in.

```bash
!git clone https://github.com/ohlc-ai/bing-images-download.git
```
You will see a new folder has been created with all the repository files in it.

Run
```bash
%cd /content/bing-images-download
```
Voila! You are in repo's directory.

```bash
pip install -r requirements.txt
```
Now that all the required libraries are installed, it's time to install Chromium driver in your Colab notebook.

```bash
!apt install chromium-chromedriver
```
And, that's it! We will now mount our Google drive on this notebook so that images could be directly downloaded. To do that, click on Google Drive icon. It will ask for permission to mount the drive. Click on **Connect to Google Drive** to grant access.

Once Google Drive is mounted, you will see another directory - **drive**. Expand drive folder and you will probably have **My Drive** folder in it. You can create a new directory inside drive folder or in My Drive. I have created a new folder within My Drive to save images. I have named the folder dataset.

We should now change our directory since the script saves all the images in current directory/images. Copy path to the folder in which you need to download the images. For me, it's **/content/drive/My Drive/dataset**, so I will run

```bash
%cd /content/drive/My\ Drive/dataset
```
You need to change it according to your output directory folder path.

And, we're good to go!


# Use

1. For a single search term, run:
 ```bash
!python /content/bing-images-download/bing_scraper.py --search 'honeybees on flowers' --download --limit 10  --format jpg --chromedriver /usr/lib/chromium-browser/chromedriver
```
 Download up to `--limit` images supplying either a `--url`
 
You can change --limit from 10 to any number you want. That would set the limit for number of images to be downloaded per search term. Note that error-producing images may be skipped.

Here's how the output will look like:

```bash
Searching for https://www.bing.com/images/search?q=honeybees%20on%20flowers
Downloading HTML... 3499588 elements: 30it [00:24,  1.21it/s]
Downloading images...
1/10 https://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/Apis_mellifera_Western_honey_bee.jpg/1200px-Apis_mellifera_Western_honey_bee.jpg 
2/10 https://berkshirefarmsapiary.files.wordpress.com/2013/07/imgp8415.jpg 
3/10 http://www.pestworld.org/media/561900/honey-bee-foraging-side-view.jpg 
4/10 https://www.gannett-cdn.com/-mm-/da6df33e2de11997d965f4d81915ba4d1bd4586e/c=0-248-3131-2017/local/-/media/2017/06/22/USATODAY/USATODAY/636337466517310122-GettyImages-610156450.jpg 
5/10 http://4.bp.blogspot.com/-b9pA6loDnsw/TY0GjKtyDCI/AAAAAAAAAD8/jHdZ5O40CeQ/s1600/bees.jpg 
6/10 https://d3i6fh83elv35t.cloudfront.net/static/2019/02/Honey_bee_Apis_mellifera_CharlesJSharpCC-1024x683.jpg 
7/10 http://www.fnal.gov/pub/today/images05/bee.jpg 
8/10 https://upload.wikimedia.org/wikipedia/commons/5/55/Honey_Bee_on_Willow_Catkin_(5419305106).jpg 
9/10 https://cdnimg.in/wp-content/uploads/2015/06/HoneyBeeW-1024x1024.jpg 
10/10 http://www.pouted.com/wp-content/uploads/2015/03/honeybee_06_by_wings_of_light-d3fhfg1.jpg 
Done with 0 errors in 37.1s. All images saved to /content/drive/My Drive/dataset/images
```
![Output Folder](https://user-images.githubusercontent.com/26833433/75287228-dcf2ca80-57ce-11ea-9557-cc13abaff453.jpg)

2. For multiple search terms, run:
```bash
!python /content/bing-images-download/bing_scraper.py --search "honeybees on flowers, dogs, cats, bicycle" --download --limit 10  --format jpg --chromedriver /usr/lib/chromium-browser/chromedriver
```
3. For keywords list from a text or csv file, run:
```bash
!python /content/bing-images-download/bing_scraper.py --keywords_from_file /content/drive/My\ Drive/dataset/images/demo.txt --download --limit 10  --format jpg --chromedriver /usr/lib/chromium-browser/chromedriver
```
Please note that you will have to upload a list of csv or text file to /content/drive/My\ Drive/dataset/images/ folder. I have uploaded a text file named demo.txt (also available in repo's directory as demo.txt).

### Input Arguments

For the list of input arguments, check https://google-images-download.readthedocs.io/en/latest/arguments.html

### Cite

See https://github.com/ultralytics/google-images-download

### Contact

**Issues should be raised directly in the repository.** For additional questions or comments please email me at mohit@ohlc.ai
