---
title: "fireSense_EscapePredict Manual"
subtitle: "v.0.0.1"
date: "Last updated: 2025-04-08"
output:
  bookdown::html_document2:
    toc: true
    toc_float: true
    theme: sandstone
    number_sections: false
    df_print: paged
    keep_md: yes
editor_options:
  chunk_output_type: console
bibliography: citations/references_fireSense_EscapePredict.bib
link-citations: true
always_allow_html: true
---

# fireSense_EscapePredict Module

<!-- the following are text references used in captions for LaTeX compatibility -->
(ref:fireSense-EscapePredict) *fireSense_EscapePredict*



[![made-with-Markdown](figures/markdownBadge.png)](https://commonmark.org)

<!-- if knitting to pdf remember to add the pandoc_args: ["--extract-media", "."] option to yml in order to get the badge images -->

#### Authors:

Jean Marchal <jean.d.marchal@gmail.com> [aut], Ian Eddy <ian.eddy@nrcan-rncan.gc.ca> [aut, cre], Eliot McIntire <eliot.mcintire@nrcan-rncan.gc.ca> [aut], Alex M Chubaty <achubaty@for-cast.ca> [ctb]
<!-- ideally separate authors with new lines, '\n' not working -->

## Module Overview

### Module summary

Provide a brief summary of what the module does / how to use the module.

Module documentation should be written so that others can use your module.
This is a template for module documentation, and should be changed to reflect your module.

### Module inputs and parameters

Describe input data required by the module and how to obtain it (e.g., directly from online sources or supplied by other modules)
If `sourceURL` is specified, `downloadData("fireSense_EscapePredict", "..")` may be sufficient.

Table \@ref(tab:moduleInputs-fireSense-EscapePredict) shows the full list of module inputs.

<table class="table" style="color: black; margin-left: auto; margin-right: auto;">
<caption>(\#tab:moduleInputs-fireSense-EscapePredict)(\#tab:moduleInputs-fireSense-EscapePredict)List of (ref:fireSense-EscapePredict) input objects and their description.</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> objectName </th>
   <th style="text-align:left;"> objectClass </th>
   <th style="text-align:left;"> desc </th>
   <th style="text-align:left;"> sourceURL </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> fireSense_EscapeFitted </td>
   <td style="text-align:left;"> fireSense_EscapeFit </td>
   <td style="text-align:left;"> An object of class fireSense_EscapeFit created with the fireSense_EscapeFit module. </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> fireSense_IgnitionAndEscapeCovariates </td>
   <td style="text-align:left;"> data.frame </td>
   <td style="text-align:left;"> An object of class RasterStack or data.frame with prediction variables </td>
   <td style="text-align:left;"> NA </td>
  </tr>
  <tr>
   <td style="text-align:left;"> flammableRTM </td>
   <td style="text-align:left;"> SpatRaster </td>
   <td style="text-align:left;"> a raster with values of 1 for flammable pixels and 0 for nonflammable pixels </td>
   <td style="text-align:left;"> NA </td>
  </tr>
</tbody>
</table>

Summary of user-visible parameters (Table \@ref(tab:moduleParams-fireSense-EscapePredict))


<table class="table" style="color: black; margin-left: auto; margin-right: auto;">
<caption>(\#tab:moduleParams-fireSense-EscapePredict)(\#tab:moduleParams-fireSense-EscapePredict)List of (ref:fireSense-EscapePredict) parameters and their description.</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> paramName </th>
   <th style="text-align:left;"> paramClass </th>
   <th style="text-align:left;"> default </th>
   <th style="text-align:left;"> min </th>
   <th style="text-align:left;"> max </th>
   <th style="text-align:left;"> paramDesc </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> .runInitialTime </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> 0 </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> when to start this module? By default, the start time of the simulation. </td>
  </tr>
  <tr>
   <td style="text-align:left;"> .runInterval </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> 1 </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> optional. Interval between two runs of this module expressed in units of simulation time. By default, 1 year. </td>
  </tr>
  <tr>
   <td style="text-align:left;"> .saveInitialTime </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> optional. When to start saving output to a file. </td>
  </tr>
  <tr>
   <td style="text-align:left;"> .saveInterval </td>
   <td style="text-align:left;"> numeric </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> optional. Interval between save events. </td>
  </tr>
  <tr>
   <td style="text-align:left;"> .useCache </td>
   <td style="text-align:left;"> logical </td>
   <td style="text-align:left;"> FALSE </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Should this entire module be run with caching activated? This is generally intended for data-type modules where stochasticity and time are not relevant </td>
  </tr>
</tbody>
</table>

### Events

- Module initialization;
- Make predictions;

### Plotting

<!-- TODO -->
Write what is plotted.

### Saving

<!-- TODO -->
Write what is saved.

### Module outputs

Description of the module outputs (Table \@ref(tab:moduleOutputs-fireSense-EscapePredict)).

<table class="table" style="color: black; margin-left: auto; margin-right: auto;">
<caption>(\#tab:moduleOutputs-fireSense-EscapePredict)(\#tab:moduleOutputs-fireSense-EscapePredict)List of (ref:fireSense-EscapePredict) outputs and their description.</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> objectName </th>
   <th style="text-align:left;"> objectClass </th>
   <th style="text-align:left;"> desc </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> fireSense_EscapePredicted </td>
   <td style="text-align:left;"> SpatRaster </td>
   <td style="text-align:left;"> A raster with values representing escape probability </td>
  </tr>
</tbody>
</table>

### Links to other modules

Describe any anticipated linkages to other modules, such as modules that supply input data or do post-hoc analysis.

### Getting help

- <https://github.com/PredictiveEcology/fireSense_EscapePredict/issues>

## References

<!-- autogenerated from bibligraphy -->
