# ILEaccess
ILEaccess is a save file convenience packaging of IBM i libraries ILEASTIC, NOXDB and ILEUSION for convenience installation. 

ILEaccess/ ILEusion can be used to replace XMLSERVICE on IBM i as a remote data access layer via JSON REST based calls. (See API link below.)

**ILEastic** allows HTTP microservices to be created on IBM i</br>
**NOXDB** makes SQL,JSON and XML made easy for IBM i.</br>
**ILEusion** packages it all up to make IBM i data and program call services easier using JSON rest calls. ILEusion has been temporarily forked here. https://github.com/richardschoen/ILEusion</br>

For more info on these services see the sitemule Github projects:
https://github.com/sitemule

# Installing ILEACCESS library and starting an IBM i data service

Download the **ileaccess.savf** save file from the selected releases page. 

https://github.com/richardschoen/ILEaccess/releases

Upload the **ileaccess.savf** to the IFS and place it in **/tmp/ileaccess.savf**

Run the following commands to copy the save file from the IFS into a SAVF object

`CRTSAVF FILE(QGPL/ILEACCESS)`
 
`CPYFRMSTMF FROMSTMF('/tmp/ileaccess.savf') TOMBR('/qsys.lib/qgpl.lib/ileaccess.file') MBROPT(*REPLACE) CVTDTA(*NONE)`

Restore the ILEACCESS library

`RSTLIB SAVLIB(ILEACCESS) DEV(*SAVF) SAVF(QGPL/ILEACCESS)`

Starting an ILEaccess/ILEusion IBM i Data Service Instance

`ADDLIBLE ILEACCESS`

`STRILESRV JOB(ILEACCESS) 
          HOST(*ANY)     
          PORT(9999)     
          LOGIN(*YES)`

You are now ready to start developing applications in .Net, via PHP or on other platforms that can utilize the ILEusion data service. 

# Start Using ILEaccess / ILEusion

**Check out the .Net wrapper source** for accessing IBM i data using ILEusion and .Net.</br>
https://github.com/richardschoen/ILEusion-DotNet</br>

**Download Nuget package.**</br>
https://www.nuget.org/packages/ILEusionStd </br>

Hopefully other language wrappers will follow, however any language that can read and write JSON can interact with the ILEusion web service calls. 

# ILEaccess / ILEusion Documentation for Rest API Calls

https://github.com/richardschoen/ILEusion/wiki/ILEusion-API-Documentation
