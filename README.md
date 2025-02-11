# StegLip


---

Introduction to the Steganography and File Conversion Toolset

The toolset provides a set of Python scripts for file steganography, extracting hidden messages, and file format conversion using FFmpeg. The scripts steglip.py, exsteglip.py, and ficonv.py allow users to hide messages in image and audio files, retrieve hidden messages, and convert files between various formats, respectively.

This guide will walk you through the installation, setup, and usage of each of the scripts. The toolset is designed to be used from the command line, and it's fully compatible with Termux on Android and standard Linux environments. The main tools available in this package are:

1. steglip.py: Hide data within BMP images or WAV audio files.


2. exsteglip.py: Extract hidden messages from BMP images or WAV audio files.


3. ficonv.py: Convert audio and image files to various formats using FFmpeg.




---

Installation Instructions

To get started, you need to install the necessary packages and set up the toolset. This will be done automatically when running the provided bash script.

1. Updating Packages

The script starts by updating the installed packages using the following commands:

pkg update -y && pkg upgrade -y


This ensures that your Termux or Linux environment has the latest versions of the installed software packages.


2. Installing Required Software

Python: The script checks if Python is installed. If not, it installs Python:

pkg install python -y

FFmpeg: For converting files between different formats, FFmpeg is needed. If it's not installed, it will be automatically installed:

pkg install ffmpeg -y



3. Creating the Project Folder and Python Scripts

The script creates a directory for the project (~/steglip), and places three Python scripts within that directory: steglip.py, exsteglip.py, and ficonv.py.



4. Setting up Aliases

The script adds aliases to your .bashrc file so you can easily use the tool from the terminal:

alias steglip='python ~/steglip/steglip.py'
alias exsteglip='python ~/steglip/exsteglip.py'
alias ficonv='python ~/steglip/ficonv.py'



5. Applying Changes

Once the installation script is complete, source the .bashrc file to apply the changes:

source ~/.bashrc




After completing the above steps, the toolset is ready to use.


---

How to Use the Tool

This toolset is designed to be used directly from the command line. Here are the commands and their explanations:


---

1. Hiding a Message in BMP or WAV Files (steglip.py)

Command Format:

steglip -p image.bmp -m "Your secret message" -o output.bmp
steglip -a audio.wav -m "Your secret message" -o output.wav

Description:

The steglip.py script allows you to hide a message inside a BMP image or WAV audio file. The message is encoded into the least significant bits (LSB) of the image or audio file, making it invisible to the naked eye or ear.

Example 1: Hiding a Message in a BMP Image

steglip -p input_image.bmp -m "This is a secret message" -o output_image.bmp

In this example:

-p input_image.bmp: Path to the input BMP image file.

-m "This is a secret message": The message to hide in the image.

-o output_image.bmp: The path to save the new image with the hidden message.


Example 2: Hiding a Message in a WAV Audio File

steglip -a input_audio.wav -m "Hidden in audio" -o output_audio.wav

In this example:

-a input_audio.wav: Path to the input WAV file.

-m "Hidden in audio": The message to hide in the audio.

-o output_audio.wav: The path to save the new WAV file with the hidden message.



---

2. Extracting Hidden Messages from BMP or WAV Files (exsteglip.py)

Command Format:

exsteglip -f file_with_hidden_data

Description:

The exsteglip.py script extracts the hidden message from a BMP image or WAV audio file. If the file contains hidden data, the script will display the hidden message.

Example 1: Extracting a Message from a BMP Image

exsteglip -f output_image.bmp

In this example:

-f output_image.bmp: Path to the BMP image with the hidden message.


If the image contains a hidden message, the script will output it to the terminal:

Hidden message: This is a secret message

Example 2: Extracting a Message from a WAV Audio File

exsteglip -f output_audio.wav

In this example:

-f output_audio.wav: Path to the WAV file with the hidden message.


The script will display the hidden message:

Hidden message: Hidden in audio


---

3. Converting Files Between Formats (ficonv.py)

Command Format:

ficonv -a input_file -e output_format -o output_file

Description:

The ficonv.py script uses FFmpeg to convert audio and image files from one format to another. Supported formats include:

Audio: mp3, wav, amr

Image: jpg, png, jpeg


Example 1: Converting an MP3 File to WAV

ficonv -a input.mp3 -e wav -o output.wav

In this example:

-a input.mp3: Path to the input MP3 file.

-e wav: Target format to convert the file to (WAV in this case).

-o output.wav: The name of the output file in WAV format.


Example 2: Converting a JPG Image to PNG

ficonv -a input.jpg -e png -o output.png

In this example:

-a input.jpg: Path to the input JPG file.

-e png: Target format (PNG).

-o output.png: Name of the output PNG file.



---

Error Handling and Notes

1. Unsupported Formats: If you try to hide data in unsupported file formats (like .acc), you’ll get an error:

Error: .acc format is not supported.


2. Message Delimiters: The hidden message in the image or audio is terminated by a special delimiter (###). If the delimiter is not found, the script will notify you that no hidden data is found:

No hidden data found.


3. File Overwriting: If an output file already exists, it will be overwritten without warning. Be cautious when specifying output filenames.




---

Conclusion

This toolset offers an easy-to-use method for hiding and extracting messages from BMP images and WAV audio files, as well as converting files between various formats. By using simple commands, you can quickly and securely embed hidden messages inside media files or convert your files to different formats.

Final Notes:

Always ensure the format of the input files is correct.

The message you hide should not exceed the available space in the file (especially for BMP images, which may have limited capacity).

Use the ficonv.py tool to easily convert your files between different formats for use in various scenarios.


Feel free to experiment with the toolset and adapt it to your needs!

