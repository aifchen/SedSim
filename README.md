# SedSim
An Open-Source River Basin Simulation Screening Model for Reservoir Management of Sediment, Water, and Hydropower

- [Contact Us](#Contact)
- [Introduction](#Introduction)
- [Getting Started](#InstallGuide)
- [Publications using SedSim](#Pubs)

# <a name="Contact Us"></a>Contact
Thomas B. Wild, twild@umd.edu

Daniel P. Loucks, loucks@cornell.edu

George W. Annandale, george@georgewannandale.com

# <a name="Introduction"></a>Introduction

SedSim is a free, open-source, daily time step river basin simulation model for water and sediment flows, and hydropower production, in networks of reservoirs and river channels. SedSim enables water resources systems analysts and planners to explore alternative system configurations of reservoir sites, designs (i.e., outlet structures), and operating policies (SDO), and their implications for water flows, sediment transport and reservoir trapping, and hydropower production. The model uniquely enables simulation of a wide range of reservoir sediment management techniques through operational and design modifications, including flushing, sluicing, density current venting, bypassing, and dredging. SedSim can be applied in any river basin context, but is particularly useful in river basins that have experienced (or will experience) significant reservoir development. The source code (available on this repository at sedsim/SedSim_Model.xlsm) is written in the Visual Basic for Applications (VBA) language. The model requires one input file (Microsoft Excel '.xls' format), specified by the user to reflect conditions in the river basin to be modeled. The model produces output files in both ".xls" and ".csv" formats.

The following publication describes the model software:

Wild, T.B., Loucks, D.P., and Annandale, G.W. (2019). SedSim: A River Basin Simulation Screening Model for Reservoir Management of Sediment, Water, and Hydropower. Journal of Open Research Software, 7: 22. DOI: https://doi.org/10.5334/jors.261

# <a name="InstallGuide"></a>Getting Started

1. Clone SedSim from Github.

   The installation process is described in detail in the SedSim user manual in the docs folder. The basic steps are as follows:

   Users can either directly download SedSim files from the model’s github repository (https://github.com/FeralFlows/SedSim), or can “git clone” SedSim from the command prompt with the following command:

   “git clone https://github.com/FeralFlows/SedSim.git”

   If you are unfamiliar working from the command line, we suggest you try downloading Git for free here: https://git-scm.com/downloads. This download will come with “git bash”, from which you can attempt the git clone operation mentioned above. Cloning files rather than downloading them directly will enable you to pull recent SedSim repository updates directly to the local repository on your computer.

2. Open up the main (macro) workbook (SedSim.xlsm).

   Open the main SedSim model file. This file will be referred to as "SedSim_Model.xlsm" throughout this documentation for convenience, but the file can be given any name by simply right-clicking on the file icon when the file is closed and selecting "rename".
Upon opening the workbooks, you may be asked if you wish to enable macros. Click the “Enable Macros” option to allow the sediment model to execute properly.

   The image below shows the interface associated with the main workbook of the SedSim model.  It is designed to be generic so it can be used without code modification to run any input file. 

![sedsim_worksheet](/images/Capture.PNG)

3. Enable macros in security settings.

   To be certain that the SedSim model will always run on your computer, in the “SedSim_Model.xlsm” workbook, in Excel 2007 (or Excel 2010), go to File (or MS Office Button) -> Options -> Trust Center -> Trust Center Settings -> Macro Settings -> Enable All Macros. When you are finished running the model in Excel, these settings should be returned to their original status to avoid potential security threats to your computer. Alternatively, as described in step 1 above, your version of Excel may provide a warning message when you first open the SedSim model that asks if you wish to enable the currently open SedSim model Excel file to be run on your computer, among other Macro options. You can enable the model to be run on your computer this way as well. 

   The next two figures below visually depict the steps described above. From the options menu within Excel’s “File” tab, select “Trust Center”, from which you can enable macros.
   
   ![trust_center](/images/trust_center.png)
   ![trust_center](/images/trust_center_2.png)

4. Load in the input data and specify assumptions.

   Load your simulation assumptions and data into the main input file (“SedSim_Input.xlsx”) files. You can obtain an empty version of this file on the SedSim Github repository. Alternatively, you can copy the input file from the “example” directory on the paper’s Github repository (SedSim_Input_Example.xlsx) and use it as an example, replacing the example data with your data. All colored worksheets will require some input, whereas un-colored worksheets will not require user input and are instead populated during the execution of the macro. Model-related assumptions (e.g., sediment density) can be modified in the "Simulation Specifications" worksheet of the input data workbook. Please review the “Input File” section of this user manual for specific details regarding how to populate each worksheet within the main input file.

   The “SedSim_Model.xlsm” workbook is the only file that is required to be open for the simulation to run properly. The Input file and output file do not need to be opened beforehand. The input file will be opened and closed automatically when needed by the main macro, and the output file is automatically created, saved, and closed by the main macro.

5. Run the model. 

   This can be performed by clicking the "Run Model" button in the "SedSim_Model.xlsm" workbook.  During the execution of the model, the model will automatically close the input data file. The model was designed to automatically close the input data file once all data have been imported into internal arrays because keeping the input file open can exhaust the maximum memory usage limits of Excel for a large reach/reservoir network or long simulation duration. The model may produce two different types of error messages during execution: (1) a detailed error message generated by SedSim that the user must acknowledge, by clicking "OK" on the automatically generated error message box, before the simulation can proceed; and (2) an excel VBA error message, which is not likely to contain detailed instructions, and which is likely the result of improper input data specification or input/output file naming.

   Note: If the model will not run and displays an error regarding the Microsoft Excel “Solver” package, you may need to install “References” within VBA, as described in Step 5.

6. If you experience errors during a model run, install necessary “References” within Excel Visual Basic.

   Do this by opening up the "SedSim_Model.xlsm" and accessing the VBA code by selecting Alt+F11 on the keyboard. Within the “Project” menu on the left-hand side of the screen, select (VBAProject (SedSim.xlsm), click on the main model file to reveal its sub-menu, then double click the “SedSim_Model” module within the sub-menu. 

   In the main menu at the top of the screen, select Tools-->References. Find and check two boxes: (1) “Solver”, which enables sediment calibration; and (2) “Microsoft Scripting Runtime”, which enables runtime messages to be printed to a text file during model execution. Click OK to install the solver references. This is shown in the two images below.
 
   After installing these references, save the file within VBA, and close out of VBA and Excel altogether. Finally, re-open and re-run the model to see if this change permits the model to run.

   ![trust_center](/images/references.png)
   ![trust_center](/images/references_2.png)

7. Evaluate results.   

   The results of the simulation run are contained in the “SedSim_Output.xlsx” file.  Are these results reasonable given the input data?  One approach to gain confidence in the results is to create input data for relatively simple systems that should lead to obvious results, and then see if indeed they did.

# <a name="Pubs"></a>Publications using SedSim

<strong> Peer-reviewed Publications: </strong>

Wild, T.B., Loucks, D.P., and Annandale, G.W. (2019). SedSim: A River Basin Simulation Screening Model for Reservoir Management of Sediment, Water, and Hydropower. Journal of Open Research Software, 7: 22. DOI: https://doi.org/10.5334/jors.261

Wild, T.B., Loucks, D.P., Annandale, G.W., and Kaini, P. (2016). Maintaining Sediment Flows through Hydropower Dams in the Mekong River Basin. J. Water Resour. Plann. Manage, 142(1), 05015004.

Wild, T.B. and Loucks, D.P. (2015). Mitigating Dam Conflicts in the Mekong River Basin. Chapter 2 in Conflict Resolution in Water Resources and Environmental Management, edited by K.W. Hipel et al., Springer (Heidelberg), pp. 25-48. 

Wild, T.B. and Loucks, D.P. (2015). An Approach to Simulating Sediment Management in the Mekong River Basin. Chapter 12 in Sediment Matters, edited by P. Heininger and J. Cullman, Springer (Heidelberg), pp. 187-99.

Wild, T.B. and Loucks, D.P. (2014). Managing Flow, Sediment and Hydropower Regimes in the Sre Pok, Se San and Se Kong Rivers of the Mekong Basin. Water Resour. Res., 50, 5141-57.

<strong> Presentations: </strong>

Wild, T.B. and Loucks, D.P. (2014). Managing the Impacts of Reservoirs in the Mekong River Basin. In Proceedings of the ASCE World Environmental and Water Resources Congress 2014, Portland, OR, 1070-1080.

Wild, T.B. and Loucks, D.P. (2013). Managing Sediment in the Mekong River Basin: Tradeoffs between Hydropower and the Environment. In Proceedings of the ASCE World Environmental and Water Resources Congress 2013, Cincinnati, OH, 1297-1307.

Wild, T.B. and Loucks, D.P. (2012). Assessing the Potential Sediment-Related Impacts of Hydropower Development in the Mekong River Basin. In Proceedings of the ASCE World Environmental and Water Resources Congress 2012, Albuquerque, NM, 2236-2246.
