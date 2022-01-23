# Lempel-Ziv-Welch_using_C

## What is Lempel–Ziv–Welch (LZW) Algorithm ?

The LZW algorithm is a very common compression technique. This algorithm is typically used in GIF and optionally in PDF and TIFF. Unix’s ‘compress’ command, among other uses. It is lossless, meaning no data is lost when compressing. The algorithm is simple to implement and has the potential for very high throughput in hardware implementations. It is the algorithm of the widely used Unix file compression utility compress and is used in the GIF image format.
The Idea relies on reoccurring patterns to save data space. LZW is the foremost technique for general-purpose data compression due to its simplicity and versatility. It is the basis of many PC utilities that claim to “double the capacity of your hard drive”. 

## How does it work?

LZW compression works by reading a sequence of symbols, grouping the symbols into strings, and converting the strings into codes. Because the codes take up less space than the strings they replace, we get compression. Characteristic features of LZW includes, 

LZW compression uses a code table, with 4096 as a common choice for the number of table entries. Codes 0-255 in the code table are always assigned to represent single bytes from the input file.
When encoding begins the code table contains only the first 256 entries, with the remainder of the table being blanks. Compression is achieved by using codes 256 through 4095 to represent sequences of bytes.
As the encoding continues, LZW identifies repeated sequences in the data and adds them to the code table.
Decoding is achieved by taking each code from the compressed file and translating it through the code table to find what character or characters it represents.
Example: ASCII code. Typically, every character is stored with 8 binary bits, allowing up to 256 unique symbols for the data. This algorithm tries to extend the library to 9 to 12 bits per character. The new unique symbols are made up of combinations of symbols that occurred previously in the string. It does not always compress well, especially with short, diverse strings. But is good for compressing redundant data, and does not have to save the new dictionary with the data: this method can both compress and uncompress data. 
There are excellent article’s written up already, you can look more in-depth here, and also Mark Nelson’s article is commendable. 

## Implementation

The idea of the compression algorithm is the following: as the input data is being processed, a dictionary keeps a correspondence between the longest encountered words and a list of code values. The words are replaced by their corresponding codes and so the input file is compressed. Therefore, the efficiency of the algorithm increases as the number of long, repetitive words in the input data increases.

## LZW ENCODING - PSEUDOCODE
  * Initialize table with single character strings
  * P = first input character
  * WHILE not end of input stream
  * C = next input character
  * IF P + C is in the string table
  * P = P + C
  * ELSE
  * output the code for P
  * add P + C to the string table
  * P = C
  * END WHILE
  * output code for P

## Output of the Code:
![lzw_output](https://user-images.githubusercontent.com/68462343/150671218-a2cb593b-55f3-4c89-93e6-bfed23dcf100.png)
