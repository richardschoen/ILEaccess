# ILEaccess
Save file convenience packaging of IBM i libraries ILEASTIC, NOXDB and ILEUSION for convenience installation. 

**ILEastic** allows HTTP microservices to be created on IBM i
**NOXDB** makes SQL,JSON and XML made easy for IBM i.
**ILEusion** packages it all up to make IBM i data and program call services easier. 

For more info on these services see the sitemule Github projects:
https://github.com/sitemule

# Installing ILEACCESS library and starting an IBM i data service

Download the **monoi.savf** save file from the selected releases page. 

https://github.com/richardschoen/ILEaccess/releases

Upload the **ileaccess.savf** to the IFS and place it in **/tmp/ileaccess.savf**

Run the following commands to copy the save file from the IFS into a SAVF object

`CRTSAVF FILE(QGPL/ILEACCESS)`
 
`CPYFRMSTMF FROMSTMF('/tmp/ileaccess.savf') TOMBR('/qsys.lib/qgpl.lib/ileaccess.file') MBROPT(*REPLACE) CVTDTA(*NONE)`

Restore the ILEACCESS library

`RSTLIB SAVLIB(ILEACCESS) DEV(*SAVF) SAVF(QGPL/ILEACCESS)`

Starting a Data Service Instance

`ADDLIBLE ILEACCESS`

`STRILESRV JOB(ILEACCESS) 
          HOST(*ANY)     
          PORT(9999)     
          LOGIN(*YES)    

