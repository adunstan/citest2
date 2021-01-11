# !IMPORTANT!
# * Pass -m 2GB (or more) when building the image.
# * Configure Docker to use disks larger than the default 20 GB.
FROM cirrusci/windowsservercore:2019

SHELL ["powershell", "-NoLogo", "-NoProfile", "-Command"]


RUN \
    choco feature disable -n=usePackageExitCodes ; \
	choco install -y --no-progress --version=16.8.3.0 visualstudio2019buildtools

RUN \
	choco install -y --no-progress --version=1.0.0 visualstudio2019-workload-vctools  --install-args="--add Microsoft.VisualStudio.Component.VC.CLI.Support"

RUN \
    choco install -y --no-progress strawberryperl ; \
	choco install -y --no-progress winflexbison diffutils ; \
    Rename-Item -Path c:\ProgramData\chocolatey\bin\win_flex.exe flex.exe ; \
    Rename-Item -Path c:\ProgramData\chocolatey\bin\win_bison.exe bison.exe ; \
    Remove-Item C:\ProgramData\chocolatey\logs\*.* -Force -Recurse ; \
    Remove-Item C:\Users\ContainerAdministrator\AppData\Local\Temp\*.* -Force -Recurse
