# Send Serial Commands from Buffer of FB

The goal of this description is to send a list of commands which are stored in a buffer of FB.

These FB must inherit from a standart FB for identical commands.

```iecst
VAR_INPUT
   bExecute    : BOOL;

END_VAR   
   
VAR_OUTPUT
   bDone       : BOOL; 
   bBusy       : BOOL;
END_VAR
```


# Base UA_HistoryUpdate
This function block sends historical data via OPC UA to a server that supports the OPC UA HistoryUpdate function, e.g. the TwinCAT OPC UA Server. With one call you can transfer a large number of values including time stamps to the server for a node handle. The server ensures that the values transmitted are saved in a data memory and are available via Historical Access.

```iecst
VAR_INPUT
    Execute        : BOOL;
    ConnectionHdl  : DWORD;
    NodeHdl        : DWORD;
    PerformInsert  : BOOL; 
    PerformReplace : BOOL;
    DataValueCount : UINT; 
    Timeout        : TIME := DEFAULT_ADS_TIMEOUT; 
END_VA

VAR_IN_OUT
    DataValues       : ARRAY[*] OF UAHADataValue;
    ValueErrorIDs    : ARRAY[*] OF DWORD;    
END_VAR

VAR_OUTPUT
    Done      : BOOL;
    Busy      : BOOL;
    Error     : BOOL;
    ErrorID   : DWORD;
END_VAR
```