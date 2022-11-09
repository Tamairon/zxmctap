# zxmctap
ZX Spectrum TAP generator from machine code lists

### What is a TAP file?
Disk image created from a data storage tape formatted for the Commodore 64 (C64) or ZX Spectrum systems; contains an exact copy of the data from the tape in a single file; typically used for games or other types of applications.

A TAP file is simply one datablock or a group of 2 or more datablocks, one followed after the other. The TAP file may be empty. Then it has a size of 0 bytes. There's no real file size limit, like real tapes, TAP files can also contain huge amounts of data blocks.

A four possible types of TAP file we can found. For BASIC program, for Numeric and Alphanumeric array and, code or screen blocks. This utility not included support for BASIC program type file is focused only in a machine code or screen files.

1. Machine code files header
This header is 21 bytes [0 to 20]

  |  offset | Lenght | descripcion   | Aditional information |
  |---------|--------|---------------|-----------------------|
  |    0    |    1   | Always 0x13   | About 19 bytes for header              |
  |    1    |    1   | Always 0x00   |                                        |
  |    2    |    1   | Flag byte     | is 0x00 for a standard rom file        |
  |    3    |    1   | Data type     | For machine code is 0x03               |
  |    4    |   10   | Name of file  | Always are 10 fixes bytes. Null chars are filled with 0x20 |
  |    14   |    2   | Data lenght   | Litle endian data lenght               |
  |    16   |    2   | Start address |  |
  |    18   |    2   | Not used      | 0x0080 (little Endian, 32768) |
  |    20   |    1   | Checksum      | XORed type checksum                    |
  
  Example:
  
   1300   00   03   4A45542D504143202020   0020   204E   0080   C9
  \____/ \__/ \__/ \____________________/ \____/ \____/ \____/ \__/
    |     |    |             |              |      |      |     |
    |     |    |             |              |      |      |     Checksum
    |     |    |             |              |      |      Reserver, 32768 (little endian)
    |     |    |             |              |      Start address
    |     |    |             |              Data lenght
    |     |    |             Code name
    |     |    Type code
    |     FLAG type
    |     |    |             |              |      |      |     |
    




2. Screen files header



A TAP file is composed for a header and data block, with checksum on each case.

### How this application works?

### Machine code files for zxcmtap
