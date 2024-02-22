>Specifies how multiple users are to access a shared file simultaneously. 

## Andrew File System
implements complex remote file sharing semantics. Requires file close for changes to be seen. 

## Unix File System 
implements instant write changes to other users of the same open file and shares file pointers to allow multiple users to read and write concurrently. 