# python-serverless-lambda-tutorial
The steps that I use for creating and deploying python AWS Lambda functions using serverless.com framework

## Create SLS project
sls create \
  --template aws-python3 \
  --name PROJECTNAME \
  --path DIRECTORYNAME

CD into project folder

## Open project in VSCode
code .

## Open built-in terminal
Ctrl+`

## Create virtual environment
virtualenv venv --python=python3

## Enter virtual environment
source venv/bin/activate

(deactivate to leave virtual environment)

Update variables in handler.py

VSCode -> Update python (at the bottom) to venv version

Update serverless.yml file
- Change python version to venv version

plugins:
  - serverless-python-requirements

package:
  include:
    - PACKAGENAME.py
  exclude:
    - a/**

functions:
  FUNCTIONNAME:
    name: FUNCTIONNAME
    handler: handler.HANDLERNAME


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
