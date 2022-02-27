# How to get data from google sheets

Exhibit docs usually have a link to a google sheet and get it as a jsonp file. This method doesn't work anymore due to API changes.

As google says, *the Sheets v3 API has been turned down. Further information can be found at: https://cloud.google.com/blog/products/g-suite/migrate-your-apps-use-latest-sheets-api*

If you want to continue using this method of storing the data, you can change the **jsonp** output by a **csv** output either. You must publish the document as **csv** (```File > Publish in the Web > CSV```)

So the old exhibit code: 

```html
<link rel="exhibit/data"
    type="application/jsonp"
    href="https://spreadsheets.google.com/feeds/list/1QFApf8MGr-ZP-OqvKtPFUEASuaq9_vuvLOfanC4NGHQ/od6/public/basic?alt=json-in-script"
    ex:converter="googleSpreadsheets" /> 
```
should be replaced by:

```html
<link
    href="https://docs.google.com/spreadsheets/d/e/2PACX-1vQYa_HKoDuTImGTnDVU3C79Y7Fm02h8as7mXUOzJUbAyks2VzCSjr7n5TCfS9lxNKrDx_mPVl_l7Kd6/pub?gid=0&single=true&output=csv"
    type="text/csv" rel="exhibit/data"
    data-ex-properties="label,itemID,Link1,Link2,Link3,Short_Description,Long_Description,Developer,Category,Activity_Type,imageURL,Tags,Grade_Band,OA_Principle"
    data-ex-has-column-titles="true" 
    data-ex-value-separator=";" />
```

Look at the example at https://lmorillas.github.io/exhibit_tests/testoacurriculum/