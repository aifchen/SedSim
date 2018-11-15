# SedSim

- [Contact Us](#Contact)
- [Introduction](#Introduction)
- [Getting Started](#InstallGuide)
- [Model Structure](#ModelStructure)
    + [Model Structure Overview](#ModelOverview)  
    + [Model Files](#ModelFiles)
- [Input Files](#InstallGuide)
- [Output Files Files](#InstallGuide)

# <a name="Contact Us"></a>Contact
Thomas B. Wild, twild@umd.edu

Daniel P. Loucks, loucks@cornell.edu

# <a name="Introduction"></a>Introduction

SedSim is an ope-source, daily time step river basin simulation model for flow, sediment and hydropower production in networks of reservoirs and river channels. It is intended to predict in relative terms the spatial and temporal accumulation and depletion of sediment in river reaches and in reservoirs under different reservoir operating and sediment management policies. Thus, the model is expected to be used for estimating sediment transport in river basis including those that have experienced (or will experience) extensive reservoir development. The model's source code (SedSim_Model.xlsm) is written in the Visual Basic for Applications (VBA) language. The model requires one input file (Microsoft Excel '.xls' format), specified by the user to reflect conditions in the river basin to be modeled. The model produces output files in both ".xls" and ".csv" formats.

# <a name="Getting Started"></a>Getting Started

The installation process is described in detail in the SedSim wiki, as well as in the SedSim user manual in the docs folder. The basic steps are as follows:

1. Open the main (macro) file (SedSim_Model.xlsm) and adjust specifications and settings.

This file is contained in the "sedsim" folder of the repository. Within Microsoft Excel, adjust the settings to "enable macros". Within the worksheet titled "Run Model", specify the target file paths for the input and output files, and preferences for the creation of output files.

2. Load input data into the input file ("SedSim_Input.xlsx"). 

All colored worksheets within the workbook will require some input, whereas un-colored worksheets will not require user input and are instead populated during the execution of the macro. Model-related assumptions (e.g., sediment density) can be modified in the "Simulation Specifications" worksheet of the input data workbook.

The “SedSim_Model.xlsm” workbook is the only file that is required to be open for the simulation to run properly. The Input file does not need to be opened beforehand, and the output file should not be opened during execution of the macro. The input file will be opened and closed automatically when needed by the main macro, and the output file is automatically created, saved and closed by the main macro.

3. Run the Model.

This can be performed by clicking the "Run Model" button in the "SedSim_Model.xlsm" workbook. During the execution of the model, the model will automatically close the input data file. The model was designed to automatically close the input data file once all data have been imported into internal arrays because keeping the input file open can exhaust the maximum memory usage limits of Excel for a large reach/reservoir network or long simulation duration. The model may produce two different types of error messages during execution: (1) a detailed error message generated by SedSim that the user must acknowledge, by clicking "OK" on the automatically generated error message box, before the simulation can proceed; and (2) an excel VBA error message, which is not likely to contain detailed instructions, and which is likely the result of improper input data specification or input/output file naming by the user.

Note: If the model will not run and displays an error regarding the Microsoft Excel “Solver” package, you may need to install a reference to “Solver” in the VBA code. Do this by opening up the "SedSim_Model.xlsm" and accessing the VBA code by selecting Alt+F11 on the keyboard. Within the “Project” menu on the left hand side of the screen, click on the main model file to reveal its sub-menu, then double click the “SedSim_Model” module within the sub-menu. In the main menu at the top of the screen, select Tools-->References. Find and check the “Solver” box. Click OK to install the solver references. Re-run the model to see if this change permits the model to run.
