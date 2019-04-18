# EPub to Dictionary Conversion

This repository contains code examples for converting EPub books to a dictionary file for use in Sony PRS e-readers (or any other E-Reader with support for custom dictionaries). 

## Step by step Guide
If you only want to translate your book follow steps 2-5. The additional steps are for users owning a PRS-650 E-Reader

**1.** Install [PRS-Plus](https://github.com/natowi/prs-plus)
  * For the PRS-650 download [this](https://github.com/natowi/prs-plus/blob/master/downloads/PRSP_650_2.1.02alpha.zip) and run the .exe on a Windows machine. No need to do anything else on a Windows machine from here on.

**2.** Convert your EPub to a .txt file either with the following command [Calibre](https://manual.calibre-ebook.com/conversion.html) or use the command line
```sh
ebook-convert yourbook.epub stillyourbook.txt
```
**3.** Get unique words from .txt file
```python
lst = get_unique_words_from_book(fn_book)
```
**4.** Translate words from list
```python
new_list = translate_words(lst)
```
This function uses the Yandex API, which uses a free developers key.

**5.** Use [xmltodict](https://github.com/martinblech/xmltodict) to write dict back to xml or xdxf file

**6.** To transfer the dictionary to the PRS-650 use the [conversion tool](https://github.com/natowi/prs-plus/blob/master/downloads/xdxfToPrsp_1.01b.zip)
```sh
java -jar xdxfToPrsp.jar yourdict.xdxf
```
This will create a yourdict.prsdict file

**7.** Connect E-reader and transfer yourdict.prsdict to /database/system/PRSPlus/dictionary

**8.** In E-Reader PRS-Plus settings choose yourdict.prsdict as new dictionary


For a full example see [epub_to_dict.ipynb](epub_to_dict.ipynb)

# Custom dictionaries

One advantage of a custom dictionary is multi-language support as you can add every language you want as additional field to the dictionary. See here for an example of my e-reader with two languages offered as translation.
![Example of multi-language support](./media/dict_testimage.jpg)
