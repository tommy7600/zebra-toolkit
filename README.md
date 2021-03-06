### Zebra-Toolkit

A small group of objective-c classes that make it very easy to print simple labels with a bluetooth zebra printer.

`DCZPLHelper` is a class that helps you create a label without needing to worry about the details of ZPL. Currently supported functionalities are:<br>
	- Single line text<br>
	- Multi-line wrapping text<br>
	- Decorative lines and boxes<br>
	- Images (through UIImages+HexCompression)<br>
	- PDF417 barcodes
	
`DCPrinterManager` is a very minimalistic class that manages a connection with a zebra bluetooth printer.

Here is an example of how to use all of this:

```objective-c
DCZPLHelper *zplh = [DCZPLHelper alloc] initWithLabelWidth:580 labelLength:900];
[zplh moveCursorToX:10 y:10];
[zplh addText:@"Some text here" withFontHeight:50];
[zplh moveCursorByX:0 y:100];
[zplh drawHorizontalLineWithThickness:1];
/*
	add more things to the label here
*/
NSString *commands = [zplh finish];

DCPrinterManager *pm = [[DCPrinterManager alloc] init];
pm.delegate = self;
pm.commands = commands;
[pm print];
```

This project requires you to install the Zebra SDK. You can find [more information here](https://www.zebra.com/us/en/products/software/barcode-printers/link-os/link-os-sdk.html). 
