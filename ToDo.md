ver se tá no package.json
se nao existe, é global
  pega pasta global do npm
(e se for pasta system?)
pega na hora o q ta no package.json
  em bin
  ou em main
chama node e era isso





@ECHO off
SETLOCAL
CALL :find_dp0

IF EXIST "%dp0%\node.exe" (
  SET "_prog=%dp0%\node.exe"
) ELSE (
  SET "_prog=node"
  SET PATHEXT=%PATHEXT:;.JS;=;%
)

"%_prog%"  "%dp0%\..\ava\cli.js" %*
ENDLOCAL
EXIT /b %errorlevel%
:find_dp0
SET dp0=%~dp0
EXIT /b
