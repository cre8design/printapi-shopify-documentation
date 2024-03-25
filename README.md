# Shopify PrintApi Documentation

## 1. Introduction

This document aims to provide a guide about how to set up your Shopify Store in 
a manner that our PrintApi can communicate with it. The PrintApi will check 
periodically for new orders in your Shopify store that meet our requirements and 
pull them to our production facility for fulfillment.

## 2. Shopify Custom Data Attributes

You will need to create a few custom data attributes in your Shopify store to
communicate to our PrintApi which specific product and print files to use. Those 
attributes will be visible for each product/variant in your shopify admin panel
and allow you to configure how the product should be printed. To create new 
attributes you will have to navigate to:

**Shopify Admin Panel / Settings / Custom Data**

Depending on how your Store is set up you will have to create the following 
attributes for **Products**, **Variants** or both. Should the products that you 
want us to print be configurable, meaning they contain options on your side, you 
will need to create the attributes for the **Variant** section. Should the 
products not have variants you will need to create the attributes for the 
**Product** section. Should you have both, simple products and configurable 
products, you will need to create the attributes in both sections.

#### 2.1 Material

This attribute provides us with the information about the material we should use.

1. Add a new definition
2. Name it **Material**
3. Give it the namespace and key **print_api.material**
4. Select the type **Single line text**
5. Check the box **Limit to preset choices**
6. Add the following choices:
   - Plexiglas UV Glossy
   - Plexiglas UV Matte
   - Glass 4mm
   - Dibond
   - RVS
   - Fine Art Plexiglas Glossy
   - Fine Art Plexiglas Matte
   - Fine Art Plexiglas True Life
   - Wood
   - Fine Art Aluminium
   - Poster
   - Canvas 2cm
   - Canvas 4cm
   - Forex 5mm
7. Save

![Material](/images/attr_material.png)

#### 2.2 Format Width

This attribute provides us with the information about the width of the print.

1. Add a new definition
2. Name it **Format Width**
3. Give it the namespace and key **print_api.format_width**
4. Select the type **Dimension**
5. Add **20 cm** as the **minimum dimension**
6. Add **200 cm** as the **maximum dimension**
7. Save

![Format Width](/images/attr_format_width.png)

#### 2.3 Format Height

This attribute provides us with the information about the height of the print.

1. Add a new definition
2. Name it **Format Height**
3. Give it the namespace and key **print_api.format_height**
4. Select the type **Dimension**
5. Add **20 cm** as the **minimum dimension**
6. Add **200 cm** as the **maximum dimension**
7. Save

![Format Width](/images/attr_format_width.png)

#### 2.4 Frame

This attribute provides us with the information about the frame we should use.

1. Add a new definition
2. Name it **Frame**
3. Give it the namespace and key **print_api.frame**
4. Select the type **Single line text**
5. Check the box **Limit to preset choices**
6. Add the following choices:
   - None
   - Frame Black
   - Frame Blank
7. Save

![Frame](/images/attr_frame.png)

#### 2.6 Mounting System

This attribute provides us with the information about the mounting system we should use.

1. Add a new definition
2. name it **Mounting System**
3. Give it the namespace and key **print_api.mounting_system**
4. Select the type **Single line text**
5. Check the box **Limit to preset choices**
6. Add the following choices:
   - None
   - Blind Kunststoff
   - Aluminium Profile
   - Flat on the Wall
7. Save

![Mounting System](/images/attr_mounting.png)

#### 2.7 Print File URL

This attribute provides us with the information about the print file we should use.

1. Add a new definition
2. name it **Print File Url**
3. Give it the namespace and key **print_api.print_api_url**
4. Select the type **Url**
5. Save

![Mounting System](/images/attr_print_file_url.png)

## 3. Populating Product Data

It is crucial that:

a) all products and variants that you want us to print have 
the custom data attributes populated. You can do this manually from your Shopify
admin panel or use an App like **DataChamp Excel & CSV Exports** to populate 
your products and variants in bulk.

b) The combination of attributes corresponds to a variation that we sell. You 
can reference our shop https://printingambitions.com/store to see which 
variations we offer. For a quick overview you can use the ***pricelist*** tab.

## 4. Providing Print Files

You will need to provide us with the print files for each product. This file
has to follow our 
[delivery specifications](https://printingambitions.com/en/delivery-specifications) 
and has to be accessible via an url. Add the URL to the **Print File URL** to
the product/variant as the **Print File Url** attribute in your Shopify admin 
panel.

### 4.1 Google Drive

It is possible to provide us with the print files via Google Drive. To retrieve
the necessary URL follow these steps:

1. Upload your files to Google Drive
2. Release restrictions from the file
   1. Either on the file or the folder click on **Share**
   2. Set **General Access** to **Anyone with the link**
      ![Google Drive](/images/google_drive.png)
   3. Click on **Done**
3. Click on **Share** and on **Copy Link** to receive the URL

## 5. Tagging Orders

We periodically check for new orders. Orders for us are identified by the tag 
**Print**.  You can set this tag manually from your Shopify admin panel or use 
an App like **AOD Auto Tag Customer & Order** to automate the process of tagging 
orders.

## 6. Providing access to your Shopify Store

1. Navigate to **Shopify Admin Panel / Settings / Apps and sales channel / View custom apps**
2. Click on **Create an app**
3. Add a name and a developer for the app
4. Click on **Create app**
5. Click on **Configure Admin API scopes** in the **Select your access scopes to get started** section
6. Check the checkbox **read_orders** in the **Orders** section
7. Click on **Save**
8. Click on **Install App**
9. Copy and store the API access token ![Api Access Token](/images/api_access_token.png)
10. Copy and store the API key ![Api Key](/images/api_key.png)
11. Provide us with the API key and the API access token
