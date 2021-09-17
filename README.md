Below is a number of commands for smbclient and rpcclient tools that can be used either for offensive or defensive purposes as well as some Net commands for SMB sessions.
You need a valid username/password.

****************************************************************

$> smbclient -L //192.168.0.1 -U Mclovin -m SMB2/SMB3

-L = list the available shares on the box.Expect to see the default Windows Admin shares : ADMIN$ , IPC$ , C$ and any additional manualy created shares.
-m = specify whic version of the SMB protocol you want to use.
-U =specify the user account.

--------------------------------------------------------------------------

$> smbclient //192.168.0.1/IPC$ -U Mclovin -m SMB2 

Connect to the specified share (IPC$) with Mclovin user account over SMB2 protocol

--------------------------------------------------------------------------

$> smbclient //192.168.0.1/IPC$ -U SUPERBAD\\Mclovin -m SMB3

Connect to the specified share on the server (IPC$) as the SUPERBAD domain user Mclovin over SMB3

*****************************************************************************


$> rpcclient -U Mclovin 192.168.0.1

Connect to the specified system 192.168.0.1 as user Mclovin

Once you connect succesfully on the system, rpcclient provides hundreds of commands and supports Tab autocomplete as well.
e.g type enum and hit Tab twice.

most common enumeration commands

$> enumdomusers
- this command shows all users defined locally on the machine and any domain users the system knows about.Returns usernames and RIDs(suffix of the SID in hex form).admin account is always RID = 0x1f4 , or 500 in decimal.

$> eunmalsgroups domain|builtin
- this command shows groups defined on the machine.
- domain flag = domain-related groups.typically groups created on local machine either by an admin or within the domain
- builtin flag =  typically default groups defined by Microsoft

$> lsaenumsid
- Shows all users SIDs defined on the machine.

$> lookupnames Mclovin / lookupnames Administrators
- Shows SID associated with user or group name.

$> lookupsids 3500
- Shows username associated with the specified SID.

$> srvinfo
- Shows OS type and version of the machine.

$> queryuser 500
- Shows a vast amount of information about the account with RID=500 ( which means admin in this case). Info such as username,full name, last time user set the password for this acount,amount of logon failures, when was the last time user logged on etc.
- If you see a Time vaue ( e.g Logon Time,Logoff Time,password last set time etc) of 01 Jan 1970  --> that means the account has not interactively logged in on the Windows system




