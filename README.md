@echo off
title 微信多开工具
color 0a
for /f "tokens=2*" %%a in ('reg query "HKEY_CURRENT_USER\Software\Tencent\weixin" /v InstallPath 2^>nul') do (set "weixin=%%b") 
if not defined weixin echo;没有找到微信&pause&exit 
set /p "num=输入要开微信的数量:"
taskkill /f /t /im  weixin.exe
cd /d "%weixin%"
for /L %%i in (1,1,%num%) do start /b "" "%weixin%\weixin.exe" ""
exit
