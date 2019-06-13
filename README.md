**Barebones-JS**
===================

**Barebones-JS** is a Javascript SDK which allows fashion clients to use Streamoid's services without a fixed UI template. Clients can use Streamoid's SDK to build custom UI components which fit seamlessly within their own websie with the same look and feel. 

**Streamoid's services:**

The below services can be accessed via the SDK:

1) Similar: Find products that are similar to the one the user is looking at. 

**Integration**

1) Adding the SDK script

Add the below script within the **head** tag

```
(function(i,s,o,g,r,t,k,a,m){
         i['PiqitObject']=r;i['PiqitGa']=t;i['PiqitToken'] = k;i[r]=i[r]||function() {
         (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
         m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
         })(window, document, 'script', 'LOADER-URL', 'PQT', 'GA TRACKER-ID', 'CLIENT TOKEN');
```     

Please contact streamoid.support@streamoid.com to get your LOADER-URL, CLIENT TOKEN, GA TRACKER-ID

2) Enabling Analytics

a) User engagement with the widget can be tracked via the SDK. To do so, add the data-attributes shown in the below diagram to the UI elements. 

![](images/Barebones_SDK_reference.png)

The left and right arrows can be clicked upon by the user to see more recommeneded products. 

b) Clickthroughs 


**Sample usage**

Once the script has been added in the head tag as shown above, Streamoid's services can be called by invoking the below functions via the PQT_barebones namespace. 

1) Similar
```
PQT_barebones.findSimilar(<QUERY_PRODUCT_ID>,function(data){console.log(data)})
```

Here, 

**<QUERY_PRODUCT_ID>** is the id of the product which at the user is looking. Similar products or complementary products for the QUERY_PRODUCT_ID can be found via the **findSimilar** and **getOutfits** methods respectively.

**function(data){console.log(data)}** is a custom callback that receives the similar products/complementary products for the outfit as JSON in **data**. The JSON can be used to build UI elements and rendered on the fashion website as a widget. 
