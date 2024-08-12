# fscg

Format Shift Command Generator for ffmpeg.

# Purpose

This small utility aims to simplify ffmpeg command creation to aid format shifting/archival of Blu-rays and DVDs.

# Spreadsheet?!

Yes, indeed. While fscg is primarily targeted at Linux users, the development of its predecessor started while I was still on Windows on my daily driver. Since most of the logic is a simple if-then-else with a hint of lookup, I felt that writing this in any programming language (whether the result is online or offline) would a.) put unnecessary burden on my less than deep front end programming skills, b.) decrease the portability of the final solution and c.) hamper the offline and ownership first approach of physical media. Moreover, word processors have been around for quite some time and will _most likely_ outlive any flavor of the month front end solution. 

# Prerequisites to run fscg

The absolute bare minimum: Any word processor. fscg was developed in LibreOffice and is stored in the OpenDocument standard that is going strong since 2005.

100% compatibility has been verified with:
* GoogleDocs (2024-08-12)

# Recommended tools

* [MakeMKV](https://makemkv.com/) (Blu-ray/DVD archival)
* [VLC](https://www.videolan.org/vlc/) (DVD archival, media player)
* [ffmpeg](https://ffmpeg.org/) (to make use of the output)

# Other recommended resources

* [mpv](https://mpv.io/) (media player)
* [FindVUK Online Database](http://fvonline-db.bplaced.net/) (Blu-ray playback helper) 

# Limitations

## CPU Encoding

While the early predecessors of fscg targeted GPU encoding (first on nVidia, then on AMD), I slowly went back to CPU encoding as it provided ~10% smaller files at the same quality target (using H.265). An AMD GPU encoding path is still retained. However, the resulting ffmpeg command will most likely work only in Linux.

# Rationale

## Media source instead of input extension selection

The onus of fscg is format shifting/archival of physical media. Input file types are given for both Blu-ray and DVD in the process. However, fscg provides a `Custom` mode that allows other file types on the input.

## Language code usage

Believe it or not, this all comes down to convenience. ISO 639-2 codes are used to provided stream metadata in ffmpeg commands. Instead of trying to come up with a fancy replacement solution, I erred on the side of using the ISO 639-2 codes with a human readable language name provided for reference for each channel.

## Output file extension

The Matroska container was chosen due to its flexibility and ability to replay parts of an encoded file is something happens mid encoding. However, if you prefer a different format an override variable is provided for convenience.

## H.265/HEVC encoding

The codec was chosen due to wide adoption and good encoding performance. However, if you prefer a different format, the codec can be changed by updating a constant.

## Quality preset

Chosen values of 18 for Blu-rays and 22 for DVDs was chosen following a series of subjective tests. However, if you prefer a different quality preset both an override variable is provided for one time changes or a constant can be updated for more permanent changes.
