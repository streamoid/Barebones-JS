**Barebones-JS**
===================

Streamoid's **Barebones-JS** JS SDK provides 2 main features

**Feature 1: Wrapper Functions**

The wrapper functions are the JS interface to Streamoid’s web services. You can call these wrapper functions to get the JSON response for Streamoid’s web services. The contents of the response can be used to render the UI for, say, Recommendation widget. 


**Feature 2: Analytics**

In the SDK, events can be logged from the client website by the addition of a few HTML attributes, listed in the section below.

**Integration**

Please follow the below steps for integrating Streamoid JS SDK to your website 

1. Add this loader script to the head section of the html 

```
<script>
(function(i,s,o,g,r,t,a,m){i['PiqitObject']=r;i['PiqitGa']=t;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','<Loader File>','STREAMOID','<GA-ID>','<CLIENT-TOKEN>' );
</script>
```

**Loader File**  https://js.sdk.streamoid.com/webtools/static/js/barebone_loader.js

**GA-ID**  If you need the events to be logged to your Google Analytics account, you can just pass your GA-ID here

**CLIENT-TOKEN** To be provided by Streamoid

2. Add custom attributes to the web page’s relevant HTML elements

Assume the client website is integrating a recommendation widget using Streamoid’s Fashion SuperIntelligent technology and the UI is similar to the below image

![](images/Barebones_SDK_reference.png)

**RECOMMENDATION WIDGET**
For the parent div corresponding to the recommendation widget, add the following attribute and value 

Attribute: streamoid-similar-widget
Value: ProductID of the product in the current product detail page as a string

**RECOMMENDED PRODUCT**
For each div corresponding to a product inside the recommendation widget, add the following attribute and value 

Attribute: streamoid-similar-product
Value: ProductID of the recommended product as a string

**LEFT ARROW & RIGHT ARROW**
If the UI has clickable arrows to scroll right and left inside the widget, add the following attribute and value for left and right arrows respectively

Attribute: streamoid-similar-widget-left-arrow

Value: ProductID of the product in the current product detail page as a string

Attribute: streamoid-similar-widget-right-arrow

Value: ProductID of the product in the current product detail page as a string

3. Add an extra query param for each linked product URL inside the widget

 When the products inside the recommendation widget are clicked, they will be navigated to the detail page corresponding to that product. To the URL of that particular detail page, add the following query string params

?source=similar#strmd_query=<QUERY_PRODUCT_ID>#strmd_result=<RECOMMENDED_PRODUCT_ID>


**Invoking wrapper functions**

Once the script has been added in the head tag, as shown above, Streamoid's services can be called by invoking the functions in the STREAMOID_barebones namespace. 

Example:

STREAMOID_barebones.findSimilar(<QUERY_PRODUCT_ID>,function(data){console.log(data)})

Here, Similar products are found via the findSimilar method. <QUERY_PRODUCT_ID> is the id of the product for which the user is finding similar products. 

function(data){console.log(data)} is a custom callback that receives the similar products as JSON in data. The JSON can be used to build UI elements and rendered on the fashion website as a widget. 

Sample response:

{"status": {"message": "Success", "code": 1000}, "data": {"products": ["5727536", "5680638", "5709644", "5709722", "5430577"], "queryData": "5685418"}}

Here, 

status  Indicates the status of the API call 
- message: "Success" indicates that the API call has been successful

data Contains the recommended products  

- products: An array containing all of the recommended product ids 
