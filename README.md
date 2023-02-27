# Spring 2023 Side-Channel Exploration

This file contains both the general description for each major file and the description of tasking for the assessment.

## File Descriptions

* `runner.ipynb:` The primary notebook for this project. Contains a call to the notebook that handles the build process. Please complete all of your trace generation and plot generation in this notebook.

* `build.ipynb:` The notebook handling the build calls for this project. This also includes the function used to generate power traces.

* `./firmware/makefile:` The primary make file for this project, used to pull together all the dependencies and set the firmware to be built.

* `./firmware/simpleserial-base.c:` The basic firmware for this project.

* `./firmware/raw_XXX128.c:` Four additional firmware files used for a portion of the assessment

* `./firmware/.dep/, ./firmware/hal/, ./firmware/objdir-CWNANO, ./firmware/sam4s/, & ./firmware/simpleserial/:` Each of these directories contain dependencies or other important, related code. There is no expectation for applicants to explore or alter the contents of these directories. There be dragons.

## Tasks



* Run `runner.ipynb` and verify that the output data is sinusoidal in nature. 

    * Create a directory in the root of this project, `plots`. Save all plots and all other visuals there.
    * Add a title to the plot "Simpleserial_Base_Trace" and save a `.png` with an appropriate name.

* Modify the build system to accept a parameter, `FIRMWARE`, that can be used to pass the name of a firmware file directly to the build notebook. This will involve editing the `makefile`.

    * Test your modification with the `simpleserial-base.c` file as input in the `runner.ipynb` file. Physically disconnect and reconnect the hardware each time you wish to reprogram the DUT.
    * Save a plot of the newly generated data in yellow rather than red, with the title "Simpleserial_Parameter_Defined_Firmware_Trace" and save a copy of the figure.
    * Using the two generated plots, conduct a visual analysis. Do you notice any striking differences between the two plots? If so, what does your intuition suggest might cause this?
  
* Modify `simpleserial-base.c` to do an identical operation, utilizing a looping construct rather than repeated application of the same operation.
    * After the refactor, create a plot of a newly generated trace titled "Simpleserial_Loop_Trace" and save a copy of the figure.

* Using the `raw_adds128.c` and `raw_subs128.c` firmware files, create plots of their traces with an appropriate title. Save each of the plots with an appropriate name. Make sure to re run the cell with `%run "build.ipynb` after changing the `FIRMWARE` parameter.

    * At this stage, you may find it useful to change how much of each power trace is being displayed. One suggestion might be to plot the first 1000 elements of each trace.

* Both `raw_mults128.c` and `raw_divs128.c` contain a typing error associated with the computation being preformed. Without modifying the operations, fix the issue and complete plots similar to the previous step. Save each of the plots with an appropriate name.
* Using your four plots, one for each operation, conduct a visual analysis. Can you differentiate one operation from another, strictly from a single power trace?
* Using your firmware file of your choice from those provided, write a function that generates 100 traces. Plot them on a single plot with an opacity of 0.01. Save this file as `100_Trace_MyFirmwareChoice`, with the name of your chosen operation in place of `MyFirmwareChoice`.

    * A shell of this function is given in `README.md`, you may modify it to the extent you see fit.

    * At this stage, if there are any additional modification or exploration you would like to conduct please feel free to do so. Include any additional analysis you see fit.

## Application Solutions

Please include solutions to questions posed through the tasks in this section, written in full, clear sentences.
