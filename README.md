### Export a DataGate file to CSV with ASNA Visual RPG

This Visual RPG program exports a file to a CSV comma-separated text file. It  uses the [`DGFileReader`](https://github.com/ASNA/ASNA.DataGateHelper) class to read the file it exports. 

>[See the C# version of this example](https://github.com/ASNA/cs-version-of-export-dg-to-csv). 

>[See the repo that provides the DGFileReader ](https://github.com/ASNA/ASNA.DataGateHelper). This repo's README provides more technical detail.

Export a DataGate file to either a comma- or tab-separated file.


    Export a DataGate file to CSV

    Flag                  ShortHand  Required  Description
    --------------------  ---------  --------  ---------------------------------------------
    --databasename           -d        True    Database Name
    --library                -l        True    Library name (or *LIBL if using a library list)
    --file                   -f        True    File name
    --outputpath             -p        False   Output path--defaults to current user's Documents path
    --noheadings             -nh       False   Do not include first row with field names
    --showprogress           -sp       False   Show export progress
    --tabdelimiter           -t        False   Use tab as field delimiter
    --writeschemafile        -s        False   Write schema file
    --pause                  -ps       False   Pause screen after export--usually for debugging purposes
    --help                   -h                Show this help

> Command lines are continued below for readability.

Usage using default values:

    exporttocsv --databasename  <databasename>
                --library <library>
                --file  <file> 

Usage using some optional  values:

    exporttocsv --databasename  <databasename>
                --library <library>
                --file  <file> 
                --outputpath "c:\users\roger\documents\exported_files
                --noheadings 
                --showprogress

In the output file, the Database Name has any special characters removed to make it work as part of a Windows filename. For example, "*PUBLIC/DG Net Local" gets translated to "public_dg_net_local" in the output file name.

## A note about specifying path names on the command line

If you provide a value for the `--outputpath` argument that ends with a backslash (\) followed by a double quote:

    "c:\users\roger\documents\exported_files\" 

The command line arguments from there on get all hosed up.     

The problem is that [Windows interprets a double quote preceded by a backslash (\") as a literal double quote mark.](https://docs.microsoft.com/en-us/cpp/c-language/parsing-c-command-line-arguments?view=msvc-160) Crazy, huh. 

There isn't any way to catch this issue before Windows reports it as an illegal character in the path. 

This program watches for the output path to valid, and if it isn't issues a message to remind the user to remove a trailing slash followed by a double quote. 

## Dependencies

This program uses the [`ArgyBargy` command line processor.](https://github.com/rogerpence/ArgyBargy). This is a C# project that you'll need to download and compile. You don't need to write any code, just download the `ArgyBargy` project and compile it. You can ignore the `TestArgyBargySpike` project (that is `ArgyBargy's` unit test project). After you compile `ArgyBargy`, set a reference to its `ArbyBargy.dll` in this project.

## .NET Framework version. 

This program requires at a minimum .NET Framework version 4.6.1. 


