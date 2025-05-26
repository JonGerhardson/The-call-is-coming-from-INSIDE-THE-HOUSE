#This is not a security tool. It is not a lock. It is more like a whoopie cushion to place under your doormat. 

## It replaces the EXIF data of one or many photos with fake data to make it look like the pic was shot on an iPhone 4 in 2020. It sets the geolocation metadata to a point within 100 meters of a randomly selected ICE field office. (Bypass that part with flag --mr-peterman when running, and your location will be set instead to deep in the jungles of Myanmar!  

### THIS WILL PROBABLY NOT PROVIDE YOU WITH ANY ADVANCED SECURITY. IT MIGHT BE BETTERT IF IT WORKED ON A PHONE. 


## Features

* **EXIF Manipulation**: Sets a wide range of EXIF tags to simulate an iPhone 4 (Make, Model, Software, camera settings, etc.).
* **GPS Data**:
    * Can randomly select GPS coordinates and elevation from a user-provided CSV file.
    * Can "fuzz" (slightly randomize) the selected CSV coordinates.
    * Alternatively, can use hardcoded GPS coordinates (via `--mr-peterman` flag).
* **Date/Time Control**: Sets EXIF internal timestamps (DateTimeOriginal, CreateDate, ModifyDate, SubSec, Offset) and updates file system modification/access timestamps.
* **Image Resizing/Cropping**:
    * Can resize or crop input images to iPhone 4 dimensions (2592x1936 or 1936x2592).
    * Modes: `auto` (default, decides based on aspect ratio), `scale` (fits image, may pad), `crop` (fills dimensions by cropping).
* **Thumbnail Embedding**: Attempts to generate and embed an EXIF thumbnail (192x144 pixels).
* **Batch Processing**: Can process multiple input image files at once.
* **Customizable Output**:
    * Output filenames can be sequential (`IMG_0001.JPG`, `IMG_0002.JPG`, ...) or random (`IMG_XXXX.JPG`).
    * Output directory can be specified.
* **XMP Stripping**: Removes existing XMP metadata to avoid conflicts or giveaways like `XMPToolkit`.

## Prerequisites

Before running the script, ensure the following tools are installed and accessible in your system's PATH:

* **Bash**: The script is written for Bash.
* **ExifTool**: Essential for reading and writing EXIF metadata. ([https://exiftool.org/](https://exiftool.org/))
* **ImageMagick**: Used for image resizing/cropping (`convert` command) and getting image dimensions (`identify` command). ([https://imagemagick.org/](https://imagemagick.org/))
* **bc**: Basic Calculator, used for floating-point arithmetic in GPS fuzzing and aspect ratio calculations. (Usually installed by default on Linux/macOS).

## Usage

Save the script to a file (e.g., `set_photo_metadata.sh`) and make it executable:
`chmod +x set_photo_metadata.sh`

**Command Syntax:**
