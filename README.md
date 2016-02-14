# InsightlyGoogleSheets
Tools that provide a means to download data and update changes from/to Insightly using Google Sheets

The bulk of the heavy lifting here is done by the excellent utility script by Trevor Lohrbeer known as ImportJSON. This script is designed to be run from within the Google Sheets environment, and functions very much like the built-in functions IMPORTRANGE,IMPORTHTML,IMPORTFEED, or IMPORTDATA, except it works with Java Script Object Notation (JSON) as its delivery, which has become the "de facto" data interchange format in today's Internet.

While Insightly can talk XML, API users are strongly encouraged to use JSON, and hence the approach outlined here.

You can get ImportJSON here: https://github.com/fastfedora/google-docs

The utility "out of the box" won't work without a bit of tweeking; namely, given that the Insightly API requires a key be supplied to grant access, this key has to be made available to the ImportJSON library. You can find your user specific API key under the "User Settings" choice from the Insightly menu on the top right of the screen, when logged into the application. It is a series of numbers that looks something like this:

63a6b23a-33c5-4ed3-9437-9256rv7b3f52 (note, this is NOT a real key!)

If you don't want to have to provide this value each time you make a call, the easiest way to address this is to embed it in the ImportJSON script itself (which is what I've done). Once you have loaded the script into your Google Sheet (or if you copy the one I have here as a template), find and adjust the ImportJSONAdvanced function as follows:

function ImportJSONAdvanced(url, fetchOptions, query, parseOptions, includeFunc, transformFunc) {
  
  var AccessOptions =
      {
        // the below call to getProperty ONLY works when called from within the scripting environment
        // if calling from an external agent then either hardcode the Inxightly API or pull it in some other way 
        // "headers" : {"Authorization": "Basic "+Utilities.base64Encode(UserProperties.getProperty("AccessToken"))}
        
        "headers" : {"Authorization": "Basic "+Utilities.base64Encode("63a6b23a-33c5-4ed3-9437-9256rv7b3f52")}
      }
  
  var jsondata = UrlFetchApp.fetch(url, AccessOptions);

where you will embed YOUR API key in where this bogus one is now stored (in the template the key is coded as "xxx"). The template is here:

https://docs.google.com/spreadsheets/d/1iW_uVFXteit5wspyTKuYFITppFpBzlpLdApq4McqSrI/edit?usp=sharing
