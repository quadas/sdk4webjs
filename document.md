# Web SDK Documentation
## Host
The Host is the site-owned domain (or domains) on which content is displayed for an end user who accesses the content typically by way of a Web browser, also known as name "Publisher". Global namespace: vat
Publisher page:
```
<!DOCTYPE html>
    <head>
    </head>
    <body>

    <!-- Publisher Content -->

    <!-- Set placement size -->
    <div id="XXX_YYYYYYY" type="int"></div>

    <!-- For a better style and control it, use a div -->
    <div style="{{whatever your style to controller ad}}">
        <div id="XXX_KKKKKKK" size="320x50"></div>
    </div>

    <!-- Vpadn SSP SDK Script -->
    <script type="text/javascript" src="//m.vpadn.com/ssp/vat.js"></script>
    <script>vat.addPlacement('XXX_YYYYYYY');vat.addPlacement('XXX_KKKKKKK');vat.load();</script> 
    </body>
</html>
```

## SSP Export Tag
Export Tag: (Banner)
```
<div id="XXX_YYYYYYY" size="320x50"></div>
<script type="text/javascript" src="//m.vpadn.com/ssp/vat.js"></script>
<script>vat.addPlacement('XXX_YYYYYYY');vat.load();</script>
```
Export Tag: (Interstitial)
```
<div id="XXX_YYYYYYY" type="int"></div>
<script type="text/javascript" src="//m.vpadn.com/ssp/vat.js"></script>
<script>vat.addPlacement('XXX_YYYYYYY');vat.load();</script>
```

* HTML4 does not support this tag, HTML5 does.
* To customize ad layout, publisher should use another <block></block> to wrap the tag, and given the block css style. (Example show above section)
* Doesn't support Asynchronous Syntax at this moment.
* Place the whole Tag inside <body></body> where the AD slot located. (Not need to worry about Interstitial, it will show on top)
* vat.load() should has only 1 in a page.
* JSONP - JSONP lacks error handling, it is not able to detect response (error) status code in 4xx 5xx.

## Parameter/Macro Use
| Name | Description |Value Example|Optional or Mandatory|Default|
|--------|--------|--------|--------|--------|
|  id|     Platform ID_Placement ID   |XXX_YYYYYY|Mandatory|string identifier that can only contain following characters: 0-9, a-z, A-Z|
|size|ad size (320X50, 728X90, 468X60, 300X250，336X280，468x60，728x90)|320x50|Optional|(real size depends on response given value)|
|type|ad type|banner|Optional|banner|
|test|test request (1-response test ad)|1|Optional|0|

## Interface API for Publisher
| Method Name | Description |Usage|
|--------|--------|--------|
|addPlacement|Add Placement (Ready for Request)|vat.addPlacement(placement_id)|
|load|Invoke the ad request and display all ads.(Executing fetchAds and showPlacement)|vat.load()|
|fetchAds|Perform an asynchronous ad request for specific ad|vat.fetchAds(placement_id)|
|showPlacement|Display specified ads in the anchor locations.|vat.showPlacement(placement_id)|
|addCallback|Callback depends on the type (impression, click, load)   <br/>   `impression and click NOT SUPPORT AT CURRENT VERSION`|vat.addCallback(placement_id, "load", fn(empty))|
|addVariable|A key-value pair to add to ad requests for the ad tag|vat.addVariable('gender', 'male')|


