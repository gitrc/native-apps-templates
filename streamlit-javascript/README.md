## Introduction

This is an example template for a Snowflake Native App project which demonstrates the use of JavaScript extension code and adding Streamlit code. This template is meant to guide developers towards a possible project structure on the basis of functionality, as well as to indicate the contents of some common and useful files. 


# How to build/test this template

## Run the app
Create or update an application package in your Snowflake account, upload application artifacts to a stage in the application package, and create or update an application object in the same account based on the uploaded artifacts.
```
snow app run
```

For more information, please refer to the Snowflake Documentation on installing and using Snowflake CLI to create a Snowflake Native App.  

# Directory Structure
## `/app`
This directory holds your Snowflake Native App files.

### `/app/README.md`
Exposed to the account installing the Snowflake Native App with details on what it does and how to use it.

### `/app/manifest.yml`
Defines properties required by the application package. Find more details at the [Manifest Documentation.](https://docs.snowflake.com/en/developer-guide/native-apps/creating-manifest)

### `/app/setup_script.sql`
Contains SQL statements that are run when an account installs or upgrades a Snowflake Native App.

## `/scripts`
You can add any additional scripts such as `.sql` and `.jinja` files here. One of the common use cases for such a script is to be able to add shared content from external databases to your application package, which makes it available to be used in the setup script that runs during Snowflake Native App installation. 
_Note: As of now, `snow app init` does not render these jinja templates for you into the required files, if you decide to use them. You will have to manually render them for now._


## `/src`
This directory contains code organization by functionality, such as one distinct module for Streamlit related code. The JavaScript code is defined in the UDF from the [setup_script.sql](app/setup_script.sql) file.
```
/src
   |module-ui
   |        |-src
   |            |-ui.py
   |            |-environment.yml
```

## `snowflake.yml.jinja`
While this file exists as a Jinja template, it is the only file that will be automatically rendered as a `snowflake.yml` file by the `snow app init` command, as described in the [README.md](../README.md). `snowflake.yml` is used by Snowflake CLI to discover your project's code and interact with snowflake with all relevant privileges and grants.

For more information, please refer to the Snowflake Documentation on installing and using Snowflake CLI to create a Snowflake Native App. 

## Adding a snowflake.local.yml file
Though your project directory must have a `snowflake.yml` file, an individual developer can choose to customize the behavior of Snowflake CLI by providing local overrides to `snowflake.yml`, such as a new role to test out your own application package. This is where you can use `snowflake.local.yml`, which is not a version-controlled file.

For more information, please refer to the Snowflake Documentation on installing and using Snowflake CLI to create a Snowflake Native App. 