
# Running the Administration Application from Sources

## Prerequisites:
* Start running the [Metric Platform](./analysis-platform/index.md#running-the-analysis-platform-form-sources).

## Development Toolkits
Scava Administration is a based on Angular 6 Framework. To get started with Angular, it's better to install Angular CLI 6.1.4 tool to make application development more quicker and easier (Find more here: [https://angular.io/guide/quickstart](https://angular.io/guide/quickstart)).

````Shell
sudo npm install @angular/cli@6.1.4
````

## Get the Code

Get the latest version of the code, and checkout the `dev` branch. Please don't commit to the `master` branch: see the [Development Guidelines](../../contributors-guide/contributors-guidelignes/scava-developement-process.md#source-code-repository):




If you are using __Linux / OS X__:
````Shell
git clone https://github.com/crossminer/scava.git scava
cd scava
git checkout dev
````

If you are using __Windows__ you need to do things differently due to Windows' long file name limit. In the Git shell:
````Shell
mkdir scava
cd scava
git init
git config core.longpaths true
git add remote origin https://github.com/crossminer/scava.git
git fetch
git checkout dev
````

## Run the Administration webapp

The following instructions show how to run the dashboard web app from source:

  * Enter the `administration/scava-administration/` directory within the Scava repository.
  * Under the subdirectory `src/assets/config` edit the `externalConfig.json` file and add the configuration as following:
  ``` API Gateway Configuration
  {
    "SERVICE_URL": "${API_GATEWAY_URL}"
  }
  ```
  * Under the directory `administration/scava-administration/`, install the project dependencies using `npm install`.
  * Run the web app's embedded server using angular-cli: `ng serve`.
  * Navigate to `http://localhost:4200/`.

  
