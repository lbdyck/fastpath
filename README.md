# FastPath Readme
This partitioned dataset contains the FASTPATH ISPF command dialog package.

The members of this file are:
```
    $DOC       What you are reading
    CHANGES    Change History
    FASTPATH   Fastpath REXX Exec
    EXTISPF    Edit macro to extract the ISPF Panels from the FASTPATH
               Exec
```

## Installation recommendations:

1. copy the fastpath from the exec into a exec library concatenated to
   your sysexec or sysproc dd
2. review the fastpath customization option (find *custom*)
   - do you want to leave the ISPF Panels imbedded in the exec or
     do you want to extract them
     - copy the EXTISPF exec into your exec/clist library
     - edit the fastpath member and enter EXTISPF hlq on the command line
       - hlq is where the panels pds will be created
         hlq.PANELS
       - copy the hlq.PANELS members into your ISPPLIB dataset
       - Edit FastPath to change the customization variable to 0 to
         disable loading the panels dynamically
3. Copy the FASTPATH exec into your production rexx or clist library
4. update an ispf command table:
```
   Verb      T  Action
   FASTPATH  5  SELECT CMD(%FASTPATH)
```
