Cmod S7-25 XADC Demo
==============

Introduction
--------------

This project demonstrates how to use the Cmod S7-25's analog input pins with a MicroBlaze soft-core processor. Ten times per second, the processor collects samples from the on-chip ADC and prints voltage readings from Analog input pins AIN_32 and AIN_33 out over the USB-UART bridge. Care should be taken not to exceed the 3.3V maximum of the analog input pins.

Using This Demo
--------------
Requirements:
* [Cmod S7-20](https://store.digilentinc.com/cmod-s7-breadboardable-spartan-7-fpga-module/)
* [Vivado+SDK 2018.2 Installation](https://reference.digilentinc.com/vivado/installing-vivado/start)
* [Tera Term Installation](https://ttssh2.osdn.jp/index.html.en) or other serial terminal application
* Test circuit (not described in this document).
* MicroUSB Cable
	
Release Usage:

1. Download and extract the release ZIP archive.
2. Open the included XPR project in Vivado 2018.2 (\<archive extracted location\>/vivado_proj/Cmod-S7-25-XADC.xpr).
3. In the toolbar at the top of the Vivado window, select **File -> Export -> Export Hardware**.
4. Set "Export to" field to "<Local to Project>" and check "Include bitstream" box then click "OK".
5. In the toolbar at the top of the Vivado window, select **File -> Launch SDK**.
6. Set "Exported location" and "Workspace" fields to "<Local to Project>" then click "OK".

7. With SDK opened, wait for the hardware platform to be imported.
8. In the toolbar at the top of the SDK window, select **File -> New -> Application Project**.
9. Fill out fields as in the table below. Most of the listed values will be the defaults, but are placed in the table for completeness.
  
| Setting                                | Value                            |
| -------------------------------------- | -------------------------------- |
| Project name                           | Cmod-S7-25-XADC                  |
| Use default location                   | checked box                      |
| OS Platform                            | standalone                       |
| Target Hardware: Hardware Platform     | design_1_wrapper_hw_platform_0   |
| Target Hardware: Processor             | microblaze_0                     |
| Target Software: Language              | C                                |
| Target Software: Board Support Package | Create New (Cmod-S7-25-XADC_bsp) |

10. Click "Next", then select "Empty Application" from the list of available templates. Then click "Finish".
11. Expand the new application project (named "Cmod-S7-25-XADC") in the Project Explorer pane to the left of the SDK window.
12. Right click on the "src" subdirectory of the application project and select **Import**
13. In the "Select an import wizard" pane of the Import wizard, expand "General" and select "File System". Then click **Next**.
14. Fill out fields on the "File system" screen as in the table below. Most of the listed values will be the defaults, but are placed in the table for completeness.

| Setting                                               | Value                                     |
| ----------------------------------------------------- | ----------------------------------------- |
| From directory                                        | \<archive extracted location\>/sdk_appsrc |
| Files to import pane: sdk_appsrc                      | checked box                               |
| Into folder                                           | Cmod-S7-25-XADC/src                       |
| Options: Overwrite existing resources without warning | checked box                               |
| Options: Create top-level folder                      | unchecked box                             |

15. Click **Finish**.
<!--- Note for maintainers: This project does not require any additional application or bsp configuration. If this changes, please add the required steps to manually add them here. --->
18. Plug in a test circuit to the Cmod S7-25's analog input pins.
19. Open a serial terminal application (such as TeraTerm FIXME LINK) and connect it to the Cmod S7's serial port, using a baud rate of 9600.
20. In the toolbar at the top of the SDK window, select **Xilinx -> Program FPGA**. Leave all fields as their defaults and click "Program".
21. Right click on the "Cmod-S7-25-XADC" application project in the Project Explorer pane, and select "Run As -> Launch on Hardware (System Debugger)".
22. Refer to the statements printed via the serial terminal application for instructions on how to use the demo.

<!--- FIXME Tera Term ... --->

For more information on how this project is version controlled refer to the [Digilent Vivado Scripts Repository](https://github.com/artvvb/digilent-vivado-scripts)