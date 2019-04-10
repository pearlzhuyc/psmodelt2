# Albino Hybris

This repository contains sample customization of SAP Commerce Cloud v2.

## Contents

The customization consists of three sample SAP Hybris Commerce extensions:
- kiwi
- tiger
- albinoaddon (addon to the storefront)

The root directory contains manifest.json file, which is CCv2 Build Manifest that provides necessary build/deployment configuration.

## How to Create Your Own Storefront from Accelerator Template

By default this customization works with yacceleratorstorefront, which is the standard storefront shipped with SAP Hybris Commerce.  
However, in order to customize the storefront to your own needs, you should follow the example below (as per standard practice).

Information:  These are instructions to generate an example storefront called albino.  If you want to customize, replace the property value of `input.name` with your custom store name and  `input.package` with your custom package name in the ant properties below.

1. Clone the Albino into your `/opt/albino` directory.
2. Download a SAP Hybris Commerce and unpack it to some directory (e.g., `/opt/commerce-suite`).
3. Call
```
cd /opt/commerce-suite/hybris/bin/platform
. ./setantenv.sh
ant extensionsxml -Dinput.template=develop -Dplatform.extensions="*" -Dplatform.extensionsgen.filename=localextensions.xml
ant modulegen -Dinput.module=accelerator -Dinput.name=albino -Dinput.package=com.acme -Dplatform.extensions="*" -Dextgen.extension.path=/opt/albino/generated
```

4. Replace all occurrences of `yaccelerator` with `albino` in the `manifest.json` file.
