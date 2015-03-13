Abacus Plugin
=============

Download and Version information: http://update.sonarsource.org/plugins/abacus-confluence.html

## Description / Features
This plug-in estimates the complexity of each file in order to help you use the "abacus methodology" ("méthode des abaques" in French).
This is a methodology widely used in France to estimate the effort of changes. Customers and providers agree on the abacus at the beginning of the maintenance process.

### Example of Abacus
<table>
<tr><td colspan="2" rowspan="2">&nbsp;</td><td colspan="4">Complexity of the Change</td></tr>
<tr><td>Simple</td><td>Medium</td><td>Complex</td><td>Very complex</td></tr>
<tr><td rowspan="4">
Complexity
of the
File</td>
<td>Simple</td><td>0.1</td><td>0.3</td><td>0.8</td><td>1.5</td></tr>
<tr><td>Medium</td><td>0.3</td><td>0.6</td><td>1.8</td><td>3.0</td></tr>
<tr><td>Complex</td><td>0.6</td><td>1.2</td><td>3.0</td><td>5.0</td></tr>
<tr><td>Very complex</td><td>1.0</td><td>2.0</td><td>5.0</td><td>8.0</td></tr>
<tr>
<tr><td colspan="6">Values are in person-days.</td></tr>
</table>


Interpretation:
* According to this abacus, the effort of a complex change in a simple file would be estimated to 0.8 man days.
* According to this abacus, the effort of a very complex change in a complex file would be estimated to 5.0 man days.
Features
The complexity of a file is computed according to its cyclomatic complexity.
The default values are (estimation for a Java project):
<table>
<tr><th>Abacus Complexity</th><th>Cyclomatic Complexity</th></tr>
<tr><td>Simple</td><td><= 20</td></tr>
<tr><td>Medium</td><td>20 < X <= 50</td></tr>
<tr><td>Complex</td><td>50 < X <= 100</td></tr>
<tr><td>Very complex</td><td>> 100
</table>

See the Configuration section to set your own thresholds.

At the file level, you can either use the Abacus perspective or create a filter to display the abacus complexity measure.

At the module or project level, a widget is available to display the average abacus complexity and the abacus complexity distribution.
The abacus complexity distribution can be displayed either in number of files or percentage.

Why use this plug-in?
* To help you estimate your effort of change more quickly and accurately.
* To help settle arguments about the effort required to make a change by providing a fact-based method of understanding the complexity of each file.

## Configuration
### Properties
<table>
<tr><th>Property</th><th>Default value</th><th>Description</th></tr>
<tr><td>sonar.abacus.complexityThresholds</td><td>Simple:20;Medium:50;Complex:100;Very Complex</td>
<td>To set your own thresholds to compute the abacus complexity.<br/>
Usage: ThresholdName1:ThresholdComplexity1;ThresholdName2:ThresholdComplexity2;...;ThresholdNameN
</td></tr>
</table>

## Known Limitations
Drill-down from the average abacus complexity of a module/project does not work due to the following issue in SonarQube: SONAR-3233.
Differential views are not implemented.
Compatibility with VIEWS: as each project can define its own abacus, this plug-in does not compute the abacus complexity and distribution for a view.
