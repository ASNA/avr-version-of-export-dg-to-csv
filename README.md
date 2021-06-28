### Export a file to CSV with AVR

This program exports a file to a CSV comma-separated text file. 

Export a DataGate file to either a comma- or tab-separated file.
 
Usage:
    exporttocsv <databaseName> <library> <file> <outputPath> -noheadings -showprogress -tabdelimiter -writeschemafile
 
Required arguments--must be provided in the order shown
     <databaseName>......ASNA Database Name. If the name includes blanks surround it with double quotes.
     <library>...........Library name.
     <file>..............File name.
 
Optional arguments
     <outputPath>........Path to which output files are written. If provided, this must be the fourth 
                         argument. The default output path is the current user''s ''Documents'' folder.
 
Optional flags--flags can be provided in any order
     -help...............Show this help.
     -noheadings.........Do not include field names as first row.
     -showprogress.......Show progress as records are exported.
     -tabdelimiter.......Delimit fields with a tab character instead of a comma.
     -writeschemafile....Write schema file which shows column data types.
 
Output file is written to the target folder in the format:
     <databaseName>-<library>-<file>.txt
 
Schema file is written to the target folder in the format:
     <databaseName>-<library>-<file>.schema.txt
 
In the output file, the Database Name has any special characters removed to make it work as part of a Windows filename. For example, "*PUBLIC/DG Net Local" gets translated to "public_dg_net_local" in the output file name.

#### Implementation

This uses the [`DGFileReader`](https://github.com/ASNA/ASNA.DataGateHelper) class to read the file it exports. 
