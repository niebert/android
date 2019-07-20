## LineageOS Install Success Feedback
This is a proposal for Lineage Install Success Feedback System (LIS-FS)
### Basic Concept
Users install Lineage on a device X. Lineage is tested by the user within e.g. `Settings/LineageOS Tests` after installation and the user may decide to submit the success story about device to Lineage RESTful API that collects and processes the data. The successful installation are reported on the LineageOS/device web pages, so that the users can see, on which devices LineageOS was successfully installed. Even detailled statistics is possible, which features did not work properly. 
* **(Test Cases)** Insert clickable test-cases in the settings of LineageOS.
* **(Submit Button)** Add a submit button to the test-cases to a LineageOS backend for LIS-FS
* **(WebApp for Stastistics of Sucessful Installation)** Define a processing chain for the statistics e.g. as [Shiny WebApp and the statistics is performed with R](http://shiny.rstudio.com/).

### Test-Cases 
Collection of the test-cases for post-installation workflow. If the test cases run sucessfully the installed LineageOS.
* (Wifi) the user presses the Wifi-Connect and connect to the home Wifi network. The success is reported
* (Phone) the makes a test call with an inserted SIM card,
* ...
The test-cases are stored e.g. in JSON file
```json
{
  "hardware":{
    "chip": "...",
    ...
  },
  "tests":{
    "wifi" : true,
    "phonecall" : false,
    "testcase3": null,
    ...
  }
}
```
In the JSON for the test cases 
* `null` means test was not performed,
* `true` means test was successful,
* `false` means test failed.
There test-cases can be marked as sucessful in the user interface (GUI) within the Lineage operating system.

### Data Collection and Privacy Friendly Submission of Test Cases
With a privacy friendly approach the results of the tests are not submitted automatically to backend. 
Submission can be allowed if and only if the user grants a permission to submit the test results explicitly. 
The JSON was submitted to a [RESTful API](https://en.wikipedia.org/wiki/Representational_state_transfer) by pressing a submit button.
without submitting these data to remote backend 
Testing of the features of the operating system might take a while. Some features might not be testet by the user. Users might to decide to submit partially completed tests, so it is relevant to identify uncompleted test cases `key4testcase=null`.


### Statistics of Successful Installations and Failing Test Cases
Any installation of even buying of new device is followed by testing the offered features of the device. An incorporated test workflow after installation can added with a feedback mechanism for sharing the successful and failing installations.
* [R is a very powerful Open Source statistics tool](https://www.r-project.org/), that is used to create graphs an visualize the results of an statistical analysis.
* R as huge amount of packages and is able to read and write JSON files (see https://www.tutorialspoint.com/r/r_json_files ).
* The R scripts for the data analysis can be used directly for web front [R-Shiny](http://shiny.rstudio.com/) (see https://shiny.rstudio.com/tutorial/ ). 

## Alternatives
The information about the devices are autogenerated from a Wiki repository as YML files (e.g. https://github.com/LineageOS/lineage_wiki/blob/master/_data/devices/herolte.yml) . So instead of using a Shiny WebApp for the presentation of the success installation results, it might be more appropriate to populate the YML file with the Successful Installation Feedback data. This allows an integration in the automatic build workflow for the different devices.

## Conclusion
Post-installation tests are performed anyway to check if all desired features of phone work properly. An automated and integrated feedback mechanism could help to provide information to other users, which devices are most appropriate for LineageOS installation. 
In general the proposed feedback system uses Open Source software (R) for an integrated analysis. Lineage Install Feedback System with Backend and a web-based view on the statistical analysis for decision support of prospective Lineage Users.


