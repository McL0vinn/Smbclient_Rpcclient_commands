# smbclient_rpcclient_useful_commands

Below is a number of commands for smbclient and rpcclient tools that can be used either for offensive or defensive purposes
You need a valid username/password

****************************************************************

$> smbclient -L //192.168.0.1 -U Mclovin -m SMB2/SMB3

-L = list the available shares on the box.Expect to see the default Windows Admin shares : ADMIN$ , IPC$ , C$ and any additional manualy created shares.
-m = specify whic version of the SMB protocol you want to use
-U =specify the user account

--------------------------------------------------------------------------

$> smbclient //192.168.0.1/IPC$ -U Mclovin -m SMB2 

Connect to the specified share (IPC$) with Mclovin user account over SMB2 protocol

--------------------------------------------------------------------------

$> smbclient //192.168.0.1/IPC$ -U SUPERBAD\\Mclovin -m SMB3

Connect to the specified share on the server (IPC$) as the SUPERBAD domain user Mclovin over SMB3

---------------------------------------------------------------------------


$> rpcclient -U Mclovin 192.168.0.1

Connect to the specified system 192.168.0.1 as user Mclovin
