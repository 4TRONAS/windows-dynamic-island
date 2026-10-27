experience the ios dynamic island on windows
download the .zip file and then extract all into C:\Island 
then open terminal (powershell)
paste the following

cd $env:USERPROFILE\Downloads

Expand-Archive (Get-ChildItem .\Island-windows-widget*.zip | Sort-Object LastWriteTime -Descending | Select-Object -First 1).FullName C:\Island2 -Force

cd C:\Island2\Island

.\Island.ps1 -DebugMode

 enjoy
