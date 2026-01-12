**Brocade FOS Supplemental Documentation**

Contains tips and other non-standard Brocade documentation such as:

* Throttling considerations
* How to configure throttling
* How to correlate a login with a physical port
* Set up security certificates
* Several development considerations such as
  * Recover from too many API logins
  * Simulate a switch

 **Software Developers Tool Kit Documentation**

* Use cases and examples for the brcdapi (FOS API Driver)
* Use cases and examples for the brcddb (simple Python hierarchical relational database)

**Sample Scripts In brocade-rest-api-examples**

* Chassis Configuration
  * app_config.py: Configure the application settings. Typically only used in a batch file before debugging to enable/disable the 15 sec. HTTP timeout.
  * certs_eval.py: Evaluate security certificates.
  * certs_get.py: Retrieve and set security certificates.
  * config_upload_download.py: Example on how to upload and download configurations.
  * switch_create.py: Basic logical switch creation. Typically only used as a programmers example. For a user application, see create_swconfig.py in brocade-rest-api-applications.
  * switch_delete.py: Delete logical switches.

* Switch Configuration & Reading Switch Parameters
  * ge_stats_to_db.py: Programmers example of how to collect GE port statistics and export them to a database. See also stats_to_db.py.
  * maps_clear.py: Clear the MAPS dashboard (alerms).
  * port_config.py: Clear port statistics and set port configurations.
  * stats_to_db.py: Same as ge_stats_to_db.py but for standard port statistics.
* Zoning
  * zone_config: Example for programmers on how to configure zoning. For a user application, see zone_config.py in brocade-rest-api-applications.
  * zonecfg_enable.py: Example for programmers on how to enable a zone configuration. For a user application, see zone_config.py in brocade-rest-api-applications.


**Sample Scripts In brocade-rest-api-applications**

* Capture Data
  * capture.py: Capture data from a single chassis. Includes an option to automatically clear statistics.
  * combine.py: Combine data from the output of multiple capture.py instances into a single project.
  * multi_capture.py: Captures data from concurrently from multiple chassis and automatically combines data into a single project. Includes options to automatically generate report and clear statistics after.
  * stats_c.py: Capture port statistics from a logical switch at a user defined interval for a user defined number of samples. See stats_g.py in the Report section.
* Configuration
  * maps_config.py: Configure custom MAPS rules, groups, and policies. See also maps_report.py under Reports.
  * restore.py: Restores a chassis. Typically used as a template for configuring other chassis from a reference chassis. The advantage over the CLI configupload/configdownload commands are that the target chassis does not have to be the same chassis type as the reference chassis. It is a best effort restore.
  * restore_all.py: Generates a batch file to automatically generate restore.py instances for each chassis in a project.
  * scc_policy.py: Configure an SCC policy. Typically only used in FICON (mainframe) environments.
  * switch_config.py: Configure logical switches from a workbook.
  * switch_config_cli.py: Same as switch_config.py except instead of configuring a chassis via the API, CLI commands are generated. Useful for assisting SAN administrators in configuring a chassis without the need for API access.
* MAPS
  
* Planning
  * parse_iocp.py: Parses a mainframe IOCP in plain text. Output options include several different switch types. Used primarily for planning mainfram fabric upgrades.
  * port_count.py: Determines the port count by speed and connected device type. Typically used to determine port count and switch types when planning fabric upgrades.
* Reports
  * compare_report.py: Compares two projects.
  * maps_report.py: Generates a report of existing rules, groups, and policies. Also includes the MAPS dashboard.
  * nodefind.py: Similar to the CLI nodefind command but opperates on an entire project. Also a file as input which is convienent for finding multiple logins. Logins can be defined by alias, zone, or WWN. The use of regex matching, regex searching, and wild cards are also supported.
  * report.py: A general purpose SAN report. Includes extensive zone checking.
  * stats_g.py: Creates an Excel workbook with a worksheet that include all the captured port statistics from stats_c.py. Optionally creates a worksheet that graphs user defined port statistics based on a variety of parameters.
* Zoning
  * cli_zone.py: Zone from a plain text file with CLI zone commands.
  * mf_zone.py: Configures common mainframe zoning.
  * zone_config.py: Configures zoning from a workbook. Optionally outputs CLI. CLI is useful when access to the API is unavailable.
  * zone_merge.py: Merges the zoning database from two or more fabrics. Can use data from Cisco fabrics, but cannot configure Cisco fabrics.
  * zone_restore.py: A subset of restore.py in that it only restores zoning. This is different than configupload/configdownload in that it is chassis type independant.
* Test & Validation
  * lib_check.py: Validate that all libraries are available and at the current recommend levels.
  * login_test.py: Validate that a connection can be establish with a switch chassis.
  * scan.py: Scans a project file for chassis, logical switches, and zone configurations.
