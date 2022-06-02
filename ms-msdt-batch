SET LOGFILE=C:\RegBackup\Follina\Logs\%date:~-4,4%%date:~-7,2%%date:~-10,2%.log
SET FLAG=0

IF NOT EXIST C:\RegBackup\Follina\ (
    mkdir C:\RegBackup\Follina\
    mkdir C:\RegBackup\Follina\Logs
    echo *** Date: %DATE:/=-% ~~ Time:%TIME::=-% *** Created backup folder >> %LOGFILE%

)


REG QUERY HKEY_CLASSES_ROOT\ms-msdt
IF %errorlevel%==0 (
echo *** Date: %DATE:/=-% ~~ Time:%TIME::=-% *** Follina key found on %COMPUTERNAME% >> %LOGFILE%    
reg export HKEY_CLASSES_ROOT\ms-msdt C:\RegBackup\Follina\ms-msdt.reg /Y
echo *** Date: %DATE:/=-% ~~ Time:%TIME::=-% *** Exported the registry with the Follina key to C:\RegBackup\Follina\ms-msdt.reg >> %LOGFILE%    
reg delete HKEY_CLASSES_ROOT\ms-msdt /f
echo *** Date: %DATE:/=-% ~~ Time:%TIME::=-% *** Deleted the key >> %LOGFILE%   
echo *** Date: %DATE:/=-% ~~ Time:%TIME::=-% *** Script ended >> %LOGFILE%  
SET FLAG=1
)

REG QUERY HKEY_CLASSES_ROOT\ms-msdt

IF NOT %errorlevel%==0 IF NOT %FLAG%==1 echo *** Date: %DATE:/=-% ~~ Time:%TIME::=-% *** Follina key not found : Did nothing!>> %LOGFILE%
