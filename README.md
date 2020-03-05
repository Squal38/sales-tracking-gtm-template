# Kelkoo Group Sales Tracking Tag Google Tag Manager Template

This tag template makes it easy for merchants to add Kelkoo Group Sales Tracking Tag to Google Tag Manager container. This template is now available through Google's [Community Template Gallery](https://tagmanager.google.com/gallery/). If you have any questions or need any assistance with using this template, please contact your Account Manager.

### Contents: 
* [Configuring your tag](#config)
* [Before setting up your tag](#preparation)
* [Sales tag variables and triggers](#datalayer)
* [Test](#test)

----

## <a name="config"></a>Configuring your tag

1. On the `Templates` tab, click on the button `Search Gallery` of the block `Tag Templates` 
1. Search for the Kelkoo Group Sales Tracking Tag, select it, and in the `Template Details` click to the button `Add to workspace`
1. Add a new tag, search for the Kelkoo Group Sales Tracking Tag custom template and select it
1. Select the "all page view" trigger for the tag
1. Save the tag


## <a name="preparation"></a>Before setting up your Kelkoo Group Sales Tracking Tag

Make sure you have a **Merchant Id** and **Country code** that you can find on the "sales tracking" page of your [Kelkoo Group Merchant Extranet](https://merchant.kelkoogroup.com/).

## <a name="datalayer"></a>Include data in your datalayer

You need to add in your "Thank you page" (the page displayed after customer payment) the following datalayer:

```
<script>
    window.dataLayer = window.dataLayer || [];
    dataLayer.push({
		"kkstrack": {
			"merchantInfo": [{ "country":'COUNTRY_CODE', "merchantId":'COMID_VALUE' }],
			"orderValue": 'ORDER_VALUE',
			"orderId": 'ORDER_ID',
			"returningUser": true,
			"basket": [
				{"productname": 'PRODUCTx_NAME',"productid": 'PRODUCTx_ID',"quantity": 'PRODUCTx_QUANTITY',"price": 'PRODUCTx_PRICE'},
				{"productname": 'PRODUCTx_NAME',"productid": 'PRODUCTx_ID',"quantity": 'PRODUCTx_QUANTITY',"price": 'PRODUCTx_PRICE'}
			]
		}
    };
</script>
```


### COUNTRY_CODE:

This is the 2-letter country code for the country on which your products are listed on Kelkoo Group: ‘at’ for Austria, ‘be’ for Belgium, ‘br’ for Brazil, ‘ch’ for Switzerland, ‘cz’ for Czech Republic, ‘de’ for Germany, ‘dk’ for Denmark, ‘es’ for Spain, ‘fi’ for Finland, ‘fr’ for France, ‘ie’ for Ireland, ‘it’ for Italy, ‘mx’ for Mexico, ‘nb’ for Flemish Belgium, ‘nl’ for Netherlands, ‘no’ for Norway, ‘pl’ for Poland, ‘pt’ for Portugal, ‘ru’ for Russia, ‘se’ for Sweden, ‘uk’ for United Kingdom, ‘us’ for United States.

If you have several campaigns on Kelkoo Group, make sure to use the country code associated to your merchantId, as provided in yout Merchant Extranet.


### COMID_VALUE:

This is the unique ID representing your shop within the Kelkoo system, that your can get in your Merchant Extranet

### Multi-campaign tag

If you have several campaigns with Kelkoo Group, then you have several Merchant IDs and possibly countries. In this case you can setup the tag as followed:

```
<script>
    window.dataLayer = window.dataLayer || [];
    dataLayer.push({
		"kkstrack": {
			"merchantInfo": [,{"country":'COUNTRY_CODE1', "merchantId":'COMID_VALUE1'},{"country":'COUNTRY_CODE1', "merchantId":'COMID_VALUE1'}],
			"orderValue": 'ORDER_VALUE',
			"orderId": 'ORDER_ID',
			"returningUser": true,
			"basket": [
				{"productname": 'PRODUCTx_NAME',"productid": 'PRODUCTx_ID',"quantity": 'PRODUCTx_QUANTITY',"price": 'PRODUCTx_PRICE'},
				{"productname": 'PRODUCTx_NAME',"productid": 'PRODUCTx_ID',"quantity": 'PRODUCTx_QUANTITY',"price": 'PRODUCTx_PRICE'}
			]
		}
    };
</script>
```

### ORDER_VALUE:

This the total amount of the customer basket. It can be any real number with dot as decimal point representing the total amount of the order. Please do not add currency symbol.

### ORDER_ID:

This can be any string identifying the order. This value must be unique for each order.

#### returningUser:

This allows you to tell if it is a returning user or a new user. It is optional to provide it.


#### Optional PRODUCTx_NAME:

This can be any string that represent the product name.

#### Optional PRODUCTx_ID:

This can be any string that identify the product code.

#### Optional PRODUCTx_QUANTITY:

This can be any positive integer number representing the number of items for that specific product.

#### Optional PRODUCTx_PRICE:

This can be any real number with dot as decimal point representing the price of the single product. Please do not add currency symbol.

## <a name="test"></a>Test your integration

To test your implementation, simply simulate an order placed on your site.

    Go on your Kelkoo Merchant Extranet and log into your account then click on the link “View your Kelkoo store page” in the top right corner of the Home page
    Click on one of your offers to be redirected to your website
    Place an order on your website
    Save the source code of the confirmation page (as it appears if you do “View” -> “View source”) in case further debugging will be needed
    The next day go on your Kelkoo Merchant Extranet and log into your account
    Check in the “Statistics” menu that the sale has been recorded
    Check that all details have been correctly recorded

Important! Check regularly that sales are being registered. This is extra important to do after you have implemented updates or changes to your site.
If you encounter problems, please use our contact form to send us an email. If the test order was not properly registered in your Statistics page, please attach to your email the source code of the order confirmation page as it appeared (“View”> “View Source”). Kelkoo Sales Tracking code should normally be included.
