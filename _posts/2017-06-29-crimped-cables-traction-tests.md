---
layout: post
title: "0.8mm cables traction tests"
date: 2017-06-29
---

The iCub robot has several joints that are actuated by mechanical cables.
A few days ago I was at the IIT mechanical workshop doing some tests on the resistance of the 0.8mm cables that are used in the wrist transmission. In this post I'll be describing some details of this test.

## The cables

Transmission cable specimens were constructed from Carl-Stahl 0.8mm stainless steel cables.
The cables are terminated at both ends with cylindrical crimps that are pressed onto the cable itself.
<img src="{{ site.url }}/asset-bank/cables_traction_test_20170629_cable_col1.jpg" style="height:150pt" align="middle">


## Test setup

The test was conducted on a 50kN Zwick-Roell testing machine.
The cable was clamped in the machine's terminals with cable holders that were manufactured for the purpose.
A drawing and a photograph of the experimental setup are shown hereafter.

<img src="{{ site.url }}/asset-bank/cable_traction_test_diagram.svg" style="height:250pt" align="middle">
<img src="{{ site.url }}/asset-bank/cables_traction_test_20170616_test_machine_col1.jpg" style="height:150pt" align="middle">

The cables were pulled until failure.

The data were exported from the machine's control and data acquisition program (TestExpert) as an Excel sheet, imported and processed with the [Numpy](http://www.numpy.org), [Scipy](https://www.scipy.org/) and [Pandas](https://pandas.pydata.org/) Python libraries.

## Results

It is important to state that two out of ten tested samples failed before a significant load was reached because the crimps were not applied properly. Data from these experiments was excluded from the analysis phase.

The results of the tests are shown hereafter.
<img src="{{ site.url }}/asset-bank/data_plot.svg" style="height:250pt" align="middle">
As can be observed a maximum load of approximately 530N is reached in all test runs.
The cable elongates significantly during the test, up to 8mm.
It can be observed from the plot that the cables' behaviour is not exactly linear, and that the slope of the characteristic curve varies with its deformation.

Failed cables look as shown in the following photograph.
<img src="{{ site.url }}/asset-bank/cables_traction_test_20170629_failed_cables_col2.jpg" style="height:250pt" align="middle">

### Data processing script details

The data processing script and the Excel source data file are available in a sub-folder of on my GitHub sandbox repository.

Here are a few notes regarding the Python program.
* Loading Excel data with Pandas is extremely convenient; the command `pandas.ExcelFile` and the `pandas.io.excel.ExcelFile` methods `sheet_names` and `parse` allow to import data into Python with only a few lines of code. Although importing Pandas just for a few functions might look inelegant, achieving the same result with Numpy only would require significantly more coding.
* To round the `start_int` (of type `int`) to the closest multiple of a desired step value `step_value` the following formula can be used: `next_multiple_int = (start_int + step_value - 1) // step_value * step_value`
* To resample data the `scipy.interpolate.interp1d` can be used. To suppress bound error warnings set `bounds_error = False`
* The Numpy functions `nanmean` and `nanstd` are super useful when computing on arrays with `NaN` elements
* The `matplotlib.pyplot.fill_between` function is extremely convenient to represent the standard deviation on the plot
