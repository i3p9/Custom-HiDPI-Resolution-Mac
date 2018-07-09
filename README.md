# Custom-HiDPI-Resolution-Mac

Root PLIST File is a Sample Template for VX2260

###Step 1
`ioreg -lw0 | grep IODisplayPrefsKey`

Output will be like this: 

    "IODisplayPrefsKey" = "IOService:/AppleACPIPlatformExpert/PCI0@0/AppleACPIPCI/PEG0@1/IOPP/GFX0@0/NVDA,Display-A@0/NVDA/display0/AppleDisplay-5a63-e02c"

5a63 is `DisplayVendorId `
e02c is `DisplayProductID`

> Filename should be named after product id. So for e02c, name will be DisplayProductID-e02c.plist (Remove .plist when copying to folder)

Then, convert `DisplayVendorId `and `DisplayProductID` to decimal (They are in hex) and put them in their respective field in the plist file. 

`DisplayProductName ` can be anything you want. 

###Step 2

Resolutions! In the plist file, you have to change the `scale-resolutions` entries. For each scaled resolution there'll be two entries. The first one will be the 2x scaled res. And the second one will be the effective res.

For example if you want the effective resolution of 1440x810, in the first filed you'll enter 2880x1620.

>Note: covert decimal resolution to 8bit HEX

Example
![](https://i.imgur.com/KUELc40.png)

For multiple entries, follow the 1-2 method and keep adding `scaled` res first and `effective` second. 

##Step 3

Now that you have the plist files ready, paste the file to this location: 

`/System/Library/Displays/Contents/Resources/Overrides/DisplayVendorID-yourVendorID/`

In terminal (assuming you have the plist file in Downloads)

    sudo cp ~/Downloads/DisplayProductID-d06e.plist /System/Library/Displays/Contents/Resources/Overrides/DisplayVendorID-yourID/DisplayProductID-yourID 

Don't use this exact same line, change the VendorID and ProductID accordingly from step 1. 

Restart and change to your custom resolution. [RDM](https://github.com/avibrazil/RDM) works well for this. This is a lightning icon for HiDPI Resolutions. 

###Ending notes

> Always make sure you're putting proper resolutions because the plist file takes it literally. Don't blame me if you've done goofed. 
