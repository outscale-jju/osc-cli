# Outscale CLI

Official Outscale CLI providing connectors to Outscale API.

## Getting Started

### Prerequisites

You will need [Python 3.5+](https://www.python.org/) or later. Earlier versions including Python 2 are not supported.

### Installing from package

You can get the .whl file from releases and install it through:
```
pip install official_osc_sdk-0.1-py3-none-any.whl
```

### Installing from sources

It is a good practice to create a [dedicated virtualenv](https://virtualenv.pypa.io/en/latest/) first. Even if it usually won't harm to install Python libraries directly on the system, better to contain dependencies in a virtual environment.

```bash
virtualenv -p python3.7 .venv
source .venv/bin/activate
```

Then install osc-cli in your virtual env:
```bash
pip install -e .
```

## Configure osc-cli

The CLI requires a configuration file in `~/.osc_sdk/config.conf` The content must be a JSON whose contents look like this:
```json
{"default":
    {"access_key": "MYACCESSKEY",
     "secret_key": "MYSECRETKEY",
     "host": "outscale.com",
     "https": true,
     "method": "POST",
     "region_name": "eu-west-2",
     "version": "2018-11-19"
    }
}
```
You can add several profiles for different regions or users.

## Usage

```
osc-cli SERVICE CALL [PROFILE] [CALL-PARAMETERS]
```
or
```
osc-cli --service SERVICE --call CALL [PROFILE] [--CALL_PARAMS ...]
```
with 
* SERVICE one of the services provided by Outscale (fcu, lbu, eim, directconnect, icu)
* CALL the call you request (ie DescribeInstances)
* PROFILE the profile you want to connect to (optional)
* CALL_PARAMS [call arguments](http://docs.outscale.com) which are case-sensitive (optional)

Few examples:

## Authentication

You API crendentials are composed of an Access Key and a Secret Key located in `.osc_sdk/config.conf`.
You can list you access keys using your user and password:
```bash
osc-cli icu ListAccessKeys --authentication-method=password --login youremail@company.com --password=Y0URpAssOrd
```
