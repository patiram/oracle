This has been tested for Oracle 11.0.2g

1. Check the python architecture used:
```
python -c 'import struct;print( 8 * struct.calcsize("P"))'

    It can be 64 bit by default.

```

2. Go to http://www.oracle.com/technetwork/topics/intel-macsoft-096467.html and download following two packages
```
instantclient-basic-macos.x64-11.2.0.3.0.zip
instantclient-sdk-macos.x64-11.2.0.3.0.zip

```
3. Create new folder (oracle64) under /Users/username(your mac user name) as /Users/username(your mac user name)/oracle64
```
    Move the zip files instantclient-sdk-macos.x64-11.2.0.3.0.zip and instantclient-basic-macos.x64-11.2.0.3.0.zip to /Users/username(your mac user name)/oracle64 manually or using command line as 

mv instantclient*64* /Users/username(your mac user name)/oracle64

```
4. Go to /Users/username(your mac user name)/oracle64 from command and Unzip instantclient-basic-macos.x64-11.2.0.3.0.zip and instantclient-sdk-macos.x64-11.2.0.3.0.zip command line is recommended
```
unzip instantclient-basic-macos.x64-11.2.0.3.0.zip
unzip instantclient-sdk-macos.x64-11.2.0.3.0.zip

    It will create it will create a folder instantclient_11_2 under /Users/username(your mac user name)/oracle64 with sdk           package included in instantclient-sdk-macos.x64-11.2.0.3.0.zip
```
4. Now move to instantclient_11_2 i.e. /Users/username(your mac user name)/oracle64/instantclient_11_2 because its to create
symbolic link with some files in /usr/bin/lib/ which will be used in the installation of cx_Oracle, using following command
```
ln -s libclntsh.dylib.11.1 libclntsh.dylib
ln -s libocci.dylib.11.1 libocci.dylib
```
5. Now needs to export the environment variables for the current session as follows:

```
export ORACLE_HOME=/Users/username(your mac user name)/oracle64/instantclient_11_2
export LD_LIBRARY_PATH=$ORACLE_HOME
export DYLD_LIBRARY_PATH=$ORACLE_HOME
export PATH=$PATH:/Users/username(your mac user name)/oracle64/instantclient_11_2

    You may check your current path "instantclient_11_2" by using "pwd" command.
```
6. Go to http://sourceforge.net/projects/cx-oracle/files/ and download cx_Oracle-5.1.2.tar.gz
7. Move cx_Oracle-5.1.3.tar.gz to /Users/username(your mac user name)/oracle64/instantclient_11_2
8. Untar cx_Oracle-5.1.2.tar.gz using command as:
```
tar zxvf cx_Oracle-5.1.2.tar.gz
    so that use have /Users/username(your mac user name)/oracle64/instantclient_11_2/cx_Oracle-5.1.2 directory with all contents     of cx_Oracle-5.1.2.tar.gz
```
9. Now move to cx_Oracle-5.1.2 i.e. /Users/username(your mac user name)/oracle64/instantclient_11_2/cx_Oracle-5.1.2
10. Finally run command as:
```
sudo python setup.py build
sudo python setup.py install

    If not work then install online using 

pip install cx_Oracle

    should be successfully installed.
```
11. Finally go to python terminal as 
```
python 
    and then
import cx_Oracle
```
