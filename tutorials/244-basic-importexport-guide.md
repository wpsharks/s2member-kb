---
title: Basic Import/Export Guide
categories: tutorials
tags: importexport-tools
author: renzms
github-issue: https://github.com/websharks/s2member-kb/issues/244
---

With s2Member, you can Import/Export your Members to/from [CSV](https://en.wikipedia.org/wiki/Comma-separated_values) (a Comma-Separated Values file is a text file which can be read by any text editor, spreadsheet, or database program).

First go to **Wordpress Dashboard → s2Member → Import/Export → s2Member Options**

![screen shot 2015-08-22 at 4 07 37 pm](https://cloud.githubusercontent.com/assets/13220018/9423141/62303898-48ea-11e5-9e4a-87edf44ffe00.png)


On the backend, once there, there are 3 Tab options under the `Import/Export` tab: **User Import, User Export, and s2Member Options Import/Export**.

### For Exporting

Check under `User/Member CSV Exportation`

![screen shot 2015-08-22 at 4 22 59 pm](https://cloud.githubusercontent.com/assets/13220018/9423135/1a29edc8-48ea-11e5-98df-2c2c89efe3a4.png)

There, you'll find the following options:

1. **CSV File Preference**, by default, `Default (CSV)...` is chosen for easy re-import.
2. **Add UTF-8 Bom**, by default, `No` is chosen unless this applies to you: `If Yes—please open CSV files  with Numbers (Mac) or OpenOffice (recommended)`.
3. **CSV File Exportation**, by default starts with row `1` and limits to `1000`, and you can change these numbers depending on your needs.

The first two options you can just leave alone as default if you have no special preference regarding the CSV file type,etc.

### For Importing

Check under `User/Member CSV Importation`

Select the required CSV file, and make sure it follows the same format as in the screenshot, i.e., One Member per line, no missing fields, includes the following fields: `"ID","Username","Password","First Name","Last Name","Display Name","Email"`. Empty fields can be written as `""`, please do not remove fields.

![screen shot 2015-08-22 at 4 18 53 pm](https://cloud.githubusercontent.com/assets/13220018/9423127/9290190a-48e9-11e5-9cb6-031625658726.png)


<hr>

For more options for advanced users, please check out: 
- [Advanced Import/Export Tools](http://s2member.com/kb-article/advanced-importexport-tools/)
- [Importing/Updating Users](http://s2member.com/kb-article/importingupdating-users/)
- [How do I open the Import/Export CSV using OpenOffice?](http://s2member.com/kb-article/how-do-i-open-the-importexport-csv-using-openoffice/)
- [How do I save the Import/Export CSV with Excel on Mac OS X?](http://s2member.com/kb-article/how-do-i-save-the-importexport-csv-with-excel-on-mac-os-x/)
- [How do I force a specific EOT with the Advanced Import/Export Tools?](http://s2member.com/kb-article/how-do-i-force-a-specific-eot-with-the-advanced-importexport-tools/)
