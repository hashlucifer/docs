## GIT COMMAND

``` 
git reset HEAD --hard
git pull https://github.com/hashlucifer/abc.git
```

## JS

Injecting Script

``` javascript
var my_awesome_script = document.createElement('script');
my_awesome_script.setAttribute('src', 'http://localhost:9000/script.js');
document.head.appendChild(my_awesome_script);
```

Refused to load the script because it violates the following Content Security Policy directive
``` html 
<meta http-equiv="Content-Security-Policy" content="default-src *; style-src 'self' http://* 'unsafe-inline'; script-src 'self' http://* 'unsafe-inline' 'unsafe-eval'" />

``` 

## NODE JS | NPM | PM2

Set registry for specific private packages globally
``` sh
npm config set @private-package-name:registry http://sub.domain.com:4873/
npm config set "@fortawesome:registry" https://npm.fontawesome.com/
npm config set "//npm.fontawesome.com/:_authToken" SOME_TOKEN
```

To find versions of npm package in sub package also: `npm ls`
Start pm2 with node arguments having max old space size `pm2 start my_app.js --node-args="--max_old_space_size=500"` and for package json build 

``` json
{
    "build": "NODE_OPTIONS=--max-old-space-size=4096 cross-env react-app-rewired build"
}
```

Clear cache
 `npm cache clear --force`

## WINDOWS COMMAND

Start with https npm

``` sh
set HTTPS=true&&npm start 
```

Windows information

``` sh
WMIC BIOS GET SERIALNUMBER
WMIC CSPRODUCT GET
```

Chrome disable CROS

``` ini
"C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" --disable-web-security --disable-gpu --user-data-dir=~/chromeTemp
```

To start separate command process from command

``` bash
@start /b cmd /c  "C:\Program Files (x86)\Microsoft Office\Office16\lync.exe"
```

Find and kill specific process 

``` bash
tasklist /v | findstr /i "firefox"
tasklist /FI "IMAGENAME eq process.exe"
taskkill /f /IM process.exe
taskkill /PID 50600 /F
```

## LINUX COMMAND

Get process location

``` sh
ps -ef | grep "abc" |grep -v grep| awk '{print $2}' | xargs pwdx
```

to print environment variables:
 `printenv`
Nested file search in directory: ` find . -name '*.txt' `
Install puppeteer in linux: 
 ` sudo npm install -g puppeteer --unsafe-perm=true `
Kill all node process

``` sh
ps aux | grep -ie node | awk '{print $2}' | xargs kill -9
echo or
pkill -f 'puppeteer'
```

Kill deleted open files:

``` sh
lsof | grep 'deleted' | awk '{print $2}' | xargs kill -9
```

Check for started / open port number:
 `ls -i:9999`
Open port for public in VM: 

``` sh
sudo iptables -I INPUT -p tcp -m tcp --dport 27017 -j ACCEPT
sudo mongod --logpath /var/lib/mongodb/mongodb.log --dbpath /var/lib/mongodb
```

Check all java process: `ps -ef | grep java`

## MAC COMMAND

If hostname error comes while ssh in Mac/linux

``` sh
ssh -oHostKeyAlgorithms=+ssh-dss ctier@192.168.113.140
```

Bypass certificates Mac Chrome

``` sh
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --ignore-certificate-errors &> /dev/null &
```

Creating alias for chrome 

``` sh
nano ~/.bash_profile
alias chrome='/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --ignore-certificate-errors &> /dev/null &’
```

`ctrl+o`  `Enter`  `ctrl+x`

``` sh
source ~/.bash_profile
chrome
```

following step help me to resolve this issue on Mac Catalina OS

``` sh
sudo rm -rf $(xcode-select -print-path)
xcode-select --install
/usr/sbin/pkgutil --packages | grep CL
sudo npm install -g node-gyp
```

## VSCODE

``` json
{
    "editor.formatOnSave": true, 
    "editor.codeActionsOnSave": {
        "source.organizeImports": true
    }
}
```
