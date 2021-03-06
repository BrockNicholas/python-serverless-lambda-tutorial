## Requirements
- Serverless CLI (SLS)
- AWSCLI (AWS)
- Pip CLI (Pip)
- NPM CLI (NPM)
- Python

## Suggested
- Visual Studio Code (Code)

## Create SLS project
>sls create \\ \
>  --template aws-python3 \\ \
>  --name PROJECTNAME \\ \
>  --path DIRECTORYNAME

CD into project folder

## Open project in VSCode
`code .`

## Open built-in terminal
``Ctrl+` ``

## Create virtual environment
`virtualenv venv --python=python3`

## Enter virtual environment
`source venv/bin/activate`

(`deactivate` to leave virtual environment)

Update variables in handler.py

At the bottom toolbar of VSCode, change the python interpreter to the `venv` version. \
This will make sure the editor is working with the version you're using in your virtual environment.

Update serverless.yml file

>service: SERVICENAME
>
>provider: \
>&nbsp;&nbsp;name: aws \
>&nbsp;&nbsp;runtime: python{VERSIONNUMBER} #(e.g., python3.6)
>
>plugins: \
>&nbsp;&nbsp;\- serverless-python-requirements
>
>package: \
>&nbsp;&nbsp;include: \
>&nbsp;&nbsp;&nbsp;&nbsp;\- PACKAGENAME.py \
>&nbsp;&nbsp;exclude: \
>&nbsp;&nbsp;&nbsp;&nbsp;\- a/**
>
>functions: \
>&nbsp;&nbsp;FUNCTIONNAME: \
>&nbsp;&nbsp;&nbsp;&nbsp;name: FUNCTIONNAME \
>&nbsp;&nbsp;&nbsp;&nbsp;handler: handler.HANDLERNAME


## Install packages
This will allow you to ship packages in your SLS deployment. \
Make sure the serverless-python-requirements plugin is included in your serverless.yml file.
`npm init` \
`npm install --save serverless-python-requirements` \
\
`pip install INCLUDEDPACKAGES` \
`pip freeze > requirements.txt` 

## Run locally
`python handler.py`

## Log in to SLS account
`sls login`

## Add function to SLS Dashboard
`sls --org ORGANIZATION --app FUNCTIONNAME`

## Deploy function
`sls deploy`


## Put any parameters you want to send to your function in a .json file
e.g.,
>{ \
>  "arg": "" \
>}

## Test SLS locally
`sls invoke --function FUNCTIONNAME --path JSONTESTFILENAME.json`

## Check logs
`sls logs --function FUNCTIONNAME`

---
## Notes

## List existing deploys
`sls deploy List`

## List existing functions
`sls deploy list functions`

## Check SLS metrics
`sls dashboard`
