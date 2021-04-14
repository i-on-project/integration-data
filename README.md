[![ionproject.org](https://raw.githubusercontent.com/i-on-project/integration/master/img/i-on_logo.png)](https://www.ionproject.org)

# Introduction
The I-On initiative aims to build an extensible platform that is the reference point to the academic community, aggregating published information regarding term calendars, timetables, courses, and other items of relevance.

I-On Integration is a sub-project of the initiative and its main goal is to collect unstructured data from external sources and make the information available in a format that can be understood by other components.

This repository holds the strutured data made available by I-On Integration making it available to other I-On sub-projects.

# Data Structure

The following diagram depics the structure defined to maintain the data.

![Data Structure](https://github.com/i-on-project/integration-data/blob/experimental/img/I-On_Integration-Data_Structure.png)

The name of the folders for the schools will be based on the package naming prefix used by Java using the reversed Internet domain name for each institution qualified name.

Each school will have a folder with the academic year containing that year's academic calendar in the format `YYYY-YYYY`. The institution will also have a folder named `programmes` containing the several programmes breaked down by calendar term (semester) in the format `YYYY-YYYY-[1|2]` where the last digit refers either to the first (`1`) or the second semester (`2`).



# Resources
* [List of Academic Institutions in Portugal](https://www.dges.gov.pt/guias/indest.asp)
* [List of Higher Education Programmes in Portugal](https://www.dges.gov.pt/guias/indcurso.asp)