    ::--------------------------------------------::
    ::------ MUMBLE DEVELOPMENT ENVIRONMENT ------::
    ::------ Version 1.1 (07-30-2011)       ------::
    ::------ SCRIPT CREATED BY              ------::
    ::------  Luki - http://luki.net.pl     ------::
    ::--------------------------------------------::
    @ECHO off
    IF NOT DEFINED UPDATED_PATH SET UPDATED_PATH=0
    SETLOCAL ENABLEEXTENSIONS

    SET NEXTSTAGE=start
    :prep

    ::------ CONFIGURATION AREA ------::
    SET ENV_VSVER=10.0
    SET ENV_QTDIR=c:\dev\QtMumble
    SET ENV_VLD_DIR=c:\dev\vld
    SET ENV_MYSQL=c:\dev\mysql
    SET ENV_ICE=c:\dev\Ice

    SET MAIN_PATH=c:\dev
    SET RUN_PATH=c:\dev\mumble\release\mumble.exe
    ::------ /CONFIGURATION AREA ------::

    IF NOT %NEXTSTAGE% EQU end (IF %UPDATED_PATH% EQU 1 GOTO welcome)
    CALL "%DXSDK_DIR%\Utilities\bin\dx_setenv.cmd" x86
    CALL "%PROGRAMFILES%\Microsoft Visual Studio %ENV_VSVER%\VC\vcvarsall.bat" x86
    SET PATH=%ENV_QTDIR%\bin;c:\dev\OpenSSL\bin;c:\dev\libsndfile;c:\dev\libsndfile\bin;%ENV_MYSQL%\lib;%ENV_MYSQL%\lib\opt;%ENV_ICE%\bin\vc100;c:\dev\protobuf-2.4.1\vsprojects\Release;%PROGRAMFILES%\NASM;%ENV_VLD_DIR%\bin;%PATH%

    :welcome
    CD %MAIN_PATH%
    CLS
    TITLE Mumble Development Environment
    ECHO Welcome to Mumble Development Environment
    ECHO.
    GOTO %NEXTSTAGE%

    :start
    CD %MAIN_PATH%
    ECHO Main menu:
    ECHO  [1] Git options
    ECHO  [2] Compile
    ECHO  [3] Run
    ECHO.
    ECHO  [4] Prepare environment and exit
    ECHO.
    ECHO  [0] Exit
    ECHO.
    CHOICE /c 12340 /n /m "Select an option: "

    IF ERRORLEVEL 255 GOTO start
    IF ERRORLEVEL 5 GOTO end
    IF ERRORLEVEL 4 (
      IF %UPDATED_PATH% EQU 1 GOTO end
      ENDLOCAL
      SET UPDATED_PATH=1
      SET NEXTSTAGE=end
      GOTO prep
    )
    IF ERRORLEVEL 3 SET NEXTSTAGE=run && GOTO welcome
    IF ERRORLEVEL 2 SET NEXTSTAGE=compile && GOTO welcome
    IF ERRORLEVEL 1 SET NEXTSTAGE=git && GOTO welcome
    GOTO end

    ::------ RUN ------::
    :run
    CD %MAIN_PATH%
    TITLE Mumble Development Environment ^| Last command started: %TIME%
    ECHO Starting %RUN_PATH%
    START "mumble" "%RUN_PATH%"
    SET NEXTSTAGE=start && GOTO welcome
    GOTO end
    ::------ /RUN ------::

    ::------ COMPILE ------::
    :compile
    CD %MAIN_PATH%
    ECHO Compile menu:
    ECHO  [1] Clean
    ECHO  Compile:
    ECHO   [2] Release
    ECHO   [3] Debug
    ECHO.
    ECHO  [0] Back
    ECHO.
    CHOICE /c 1230 /n /m "Select an option: "

    IF ERRORLEVEL 255 GOTO compile
    IF ERRORLEVEL 4 SET NEXTSTAGE=start && GOTO welcome
    IF ERRORLEVEL 3 GOTO compile_debug
    IF ERRORLEVEL 2 GOTO compile_release
    IF ERRORLEVEL 1 GOTO compile_clean
    GOTO end

    :compile_debug
    TITLE Mumble Development Environment ^| Last command started: %TIME%
    cd mumble
    CALL nmake
    ECHO.
    GOTO compile

    :compile_release
    TITLE Mumble Development Environment ^| Last command started: %TIME%
    CD mumble
    CALL nmake release
    ECHO.
    GOTO compile

    :compile_clean
    TITLE Mumble Development Environment ^| Last command started: %TIME%
    CD mumble
    CALL nmake clean
    ECHO.
    GOTO compile
    ::------ /COMPILE ------::

    ::------ GIT OPTIONS ------::
    :git
    CD %MAIN_PATH%
    ECHO Git menu:
    ECHO  [1] Download sources
    ECHO  [2] Update sources
    ECHO  [3] Commit
    ECHO  [4] Create patches
    ECHO.
    ECHO  [0] Back
    ECHO.
    CHOICE /c 12340 /n /m "Select an option: "

    IF ERRORLEVEL 255 GOTO git
    IF ERRORLEVEL 5 SET NEXTSTAGE=start && GOTO welcome
    IF ERRORLEVEL 4 GOTO git_patch
    IF ERRORLEVEL 3 GOTO git_commit
    IF ERRORLEVEL 2 GOTO git_update
    IF ERRORLEVEL 1 GOTO git_download
    GOTO end

    :git_patch
    TITLE Mumble Development Environment ^| Last command started: %TIME%
    ECHO.
    cd mumble
    CALL git format-patch --find-copies-harder --patience origin
    GOTO git

    :git_commit
    TITLE Mumble Development Environment ^| Last command started: %TIME%
    ECHO.
    cd mumble
    SET /P COMMIT_DESC=Commit description:
    CALL git commit -a -m "%COMMIT_DESC%"
    GOTO git

    :git_update
    TITLE Mumble Development Environment ^| Last command started: %TIME%
    ECHO.
    CD mumble
    CALL git pull --rebase
    GOTO git

    :git_download
    TITLE Mumble Development Environment ^| Last command started: %TIME%
    ECHO.
    CHOICE /c yn /m "Are you sure"
    IF ERRORLEVEL 255 GOTO git
    IF ERRORLEVEL 2 GOTO git
    RMDIR /s /q mumble
    CALL git clone git://github.com/mumble-voip/mumble.git mumble
    CD mumble
    CALL git submodule init
    CALL git submodule update
    GOTO git
    ::------ /GIT OPTIONS ------::

    :end
    ENDLOCAL

[Category:Development](Category:Development "wikilink")