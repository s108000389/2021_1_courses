#
```
圖形化管理功能 ==> powershell

How to Manage File System ACLs with PowerShell Scripts
https://blog.netwrix.com/2018/04/18/how-to-manage-file-system-acls-with-powershell-scripts/
```
```
NTFS Permissions Types for Files and Folders

There are both basic and advanced NTFS permissions. 
   You can set each of the permissions to “Allow” or “Deny”. Here are the basic permissions:
Full Control: Users can modify, add, move and delete files and directories, 
    as well as their associated properties. In addition, 
    users can change permissions settings for all files and subdirectories.
Modify: Users can view and modify files and file properties, 
   including deleting and adding files to a directory or file properties to a file.
Read & Execute: Users can run executable files, including script
Read: Users can view files, file properties and directories.
Write: Users can write to a file and add files to directories.

Here is the list of advanced permissions:
Traverse Folder/Execute File: Users can navigate through folders to reach other files or folders, 
    even if they have no permissions for these files or folders. Users can also run executable files. 
    The Traverse Folder permission takes effect only when the group or 
    user doesn’t have the “Bypass Traverse Checking” right in the Group Policy snap-in.
List Folder/Read Data: Users can view a list of files and subfolders within 
     the folder as well as the content of the files.
Read Attributes: Users can view the attributes of a file or folder, such as whether it is read-only or hidden.
Write Attributes: Users can change the attributes of a file or folder.
Read Extended Attributes: Users can view the extended attributes of a file or folder, 
   such as permissions and creation and modification times.
Write Extended Attributes: Users can change the extended attributes of a file or folder.
Create Files/Write Data: The “Create Files” permission allows users to create files within the folder. 
    (This permission applies to folders only.) 
    The “Write Data” permission allows users to make changes to the file and overwrite existing content. 
    (This permission applies to files only.)
Create Folders/Append Data: The “Create Folders” permission allows users to create folders within a folder. 
     (This permission applies to folders only.) 
     The “Append Data” permission allows users to make changes to the end of the file, 
     but they can’t change, delete or overwrite existing data. (This permission applies to files only.)
Delete: Users can delete the file or folder. 
      (If users don’t have the “Delete” permission on a file or folder, 
      they can still delete it if they have the “Delete Subfolders And Files” permission on the parent folder.)
Read Permissions: Users can read the permissions of a file or folder, 
     such as “Full Control”, “Read”, and “Write”.
Change Permissions: Users can change the permissions of a file or folder.
Take Ownership: Users can take ownership of the file or folder. 
   The owner of a file or folder can always change permissions on it, 
   regardless of any existing permissions that protect the file or folder.
Synchronize: Users can use the object for synchronization. 
   This enables a thread to wait until the object is in the signaled state. 
   This right is not presented in ACL Editor. You can read more about it here.
```
