## Steps

### Install grunt-cli
npm install -g grunt-cli

### Fix the ReferenceError: primordials is not defined 
We encountered the same issue when updating a legacy project depending on gulp@3.9.1 to Node.js 12.

The solution
This fix enables you to use Node.js 12 with gulp@3.9.1 by overriding graceful-fs to version 4.2.2 using a npm-shrinkwrap.json file containing this:

{
  "dependencies": {
    "graceful-fs": {
      "version": "4.2.2"
    }
  }
}
And then executing npm install which will update the npm-shrinkwrap.json file.

Additional info
This issue stems from the fact that gulp@3.9.1 depends on graceful-fs@^3.0.0 which monkeypatches Node.js fs module.

This used to work with Node.js until version 11.15 (which is a version from a development branch and shouldn't be used in production).

graceful-fs@^4.0.0 does not monkeypatch Node.js fs module anymore, which makes it compatible with Node.js > 11.5.

Note that this is not a perennial solution but it helps when you don't have time to update to gulp@^4.0.0.

### run Grunt
```
grunt all
```

# Disclaimer

The United States Environmental Protection Agency (EPA) GitHub project code is provided on an "as-is" basis and the user assumes responsibility for its use. EPA has relinquished control of the information and no longer has responsibility to protect the integrity, confidentiality, or availability of the information. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by EPA. The EPA seal and logo shall not be used in any manner to imply endorsement of any commercial product or activity by EPA or the United States Government.

## Description

EPA publishes an annual air trends report in the form of an interactive web application (https://gispub.epa.gov/air/trendsreport/2019/). The report features a suite of visualization tools that allow the user to:

* Learn about air pollution and how it can affect our health and environment.
* Compare key air emissions to gross domestic product, vehicle miles traveled, population, and energy consumption back to 1970.
* Take a closer look at how the number of days with unhealthy air has dropped since 2000 in 35 major US cities.
* Explore how air quality and emissions have changed through time and space for each of the common air pollutants.
* Check out air trends where you live.
* Users will also be able to share this content across social media, with access to Facebook, Twitter, Pinterest, and other major social media sites.

This repository contains the code used throughout the 2019 trends report.

The air trends report repo has been entered into the EPA's Reusable Component Services (RCS) system at: https://ofmpub.epa.gov/sor_internet/registry2/reusereg/searchandretrieve/details/general/9717
