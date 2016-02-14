# InsightlyGoogleSheets
Tools that provide a means to download data and update changes from/to Insightly using Google Sheets

The bulk of the heavy lifting here is done by the excellent utility script by Trevor Lohrbeer known as ImportJSON. This script is designed to be run from within the Google Sheets environment, and functions very much like the built-in functions IMPORTRANGE,IMPORTHTML,IMPORTFEED, or IMPORTDATA, except it works with Java Script Object Notation (JSON) as its delivery, which has become the "de facto" data interchange format in today's Internet.

While Insightly can talk XML, API users are strongly encouraged to use JSON, and hence the approach outlined here.

You can get ImportJSON here: https://github.com/fastfedora/google-docs
