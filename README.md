### CycloneDX Plugin for Buildroot Documentation
Overview

The CycloneDX plugin for Buildroot is an official tool designed to generate a CycloneDX-compliant Software Bill of Materials (SBOM) from Buildroot projects. This documentation provides detailed instructions on how to install and use this plugin to enhance your project's security and compliance by integrating SBOMs into Fossa for vulnerability analysis.
Prerequisites

Prerequisites:

A working Buildroot environment.
Git installed on your system to clone the repository.
Access to a Fossa account for importing and analyzing the generated SBOM.

Installation
Step 1: Clone the Plugin

To install the CycloneDX plugin for Buildroot, open your terminal and execute the following command:

bash
```
git clone https://github.com/CycloneDX/cyclonedx-buildroot
```

This command clones the plugin into the cyclonedx-buildroot directory on your local machine.
Generating an SBOM
Step 1: Generate Manifest

From the Buildroot environment, run the following command to generate a manifest.csv file, which includes names, versions, and open-source licenses. The file will be outputted to /buildroot/output/legal-info:

bash
```
make legal-info
```
Step 2: Generate the CPE Data

From the Buildroot environment, run the following command to generate cpe.json. This file will be used in conjunction with the manifest.csv:

bash
```
make show-info -f cpe.json
```
Step 3: Create the CycloneDX File

Remove the sample manifest.csv file in the cyclonedx-buildroot directory. Copy the real manifest.csv and cpe.json files to the cyclonedx-buildroot directory. From the cyclonedx-buildroot directory, run the following command to generate the CycloneDX SBOM:

bash
```
python3 generateBuildrootSBOM.py -i manifest.csv -n "My Project" -v "1.2.3.4" -m "company name" -c cpe.json -o ./buildroot.json
```
Step 4: Importing the SBOM

Browse to the [SBOM upload screen](https://app.fossa.com/projects/import/upload/sbom) and select the buildroot.json file created from the clyclonedx plugin 

Sample Data can be found here 

[Sample Manaifest File ](https://github.com/rlfagan/buildroot-cyclone-dx/blob/main/manifest.csv)

[SAMPLE CPE FILE](https://github.com/rlfagan/buildroot-cyclone-dx/blob/main/cpe.json)

[SAMPLE CYCLONEDX File](https://github.com/rlfagan/buildroot-cyclone-dx/blob/main/buildroot.json)



