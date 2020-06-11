## Create SLS project
sls create \\ <br />
  --template aws-python3 \\ <br />
  --name PROJECTNAME \\ <br />
  --path DIRECTORYNAME

CD into project folder

## Open project in VSCode
`code .`

## Open built-in terminal
`Ctrl+``

## Create virtual environment
virtualenv venv --python=python3

## Enter virtual environment
source venv/bin/activate

(deactivate to leave virtual environment)

Update variables in handler.py

VSCode -> Update python (at the bottom) to venv version

Update serverless.yml file
- Change python version to venv version

service: SERVICENAME

provider:
&nbsp;&nbsp;name: aws
&nbsp;&nbsp;&nbsp;&nbsp;runtime: python{VERSIONNUMBER} #(e.g., python3.6)

plugins:
&nbsp;&nbsp;- serverless-python-requirements

package:
&nbsp;&nbsp;include:
&nbsp;&nbsp;&nbsp;&nbsp;- PACKAGENAME.py
&nbsp;&nbsp;exclude:
&nbsp;&nbsp;&nbsp;&nbsp;- a/**

functions:
&nbsp;&nbsp;FUNCTIONNAME:
&nbsp;&nbsp;&nbsp;&nbsp;name: FUNCTIONNAME
&nbsp;&nbsp;&nbsp;&nbsp;handler: handler.HANDLERNAME


## Install packages
npm init
npm install --save serverless-python-requirements

pip install INCLUDEDPACKAGES
pip freeze > requirements.txt

### Run locally
python handler.py

## Log in to SLS account
sls login

## Add function to SLS Dashboard
serverless --org ORGANIZATION --app FUNCTIONNAME

## Deploy function
sls deploy


Put JSON params in a test .json file

### Test SLS locally
sls invoke --function FUNCTIONNAME --path JSONTESTFILENAME.json

## Check logs
sls logs --function FUNCTIONNAME


** Extras **

## List existing deploys
sls deploy List

## List existing functions
sls deploy list functions

## Check SLS metrics
sls dashboard
