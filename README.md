AnchorSupply
---

<b>Check the `README.md` files in each subfolder for more information.</b>

### Concept:

Record GrowNYC supply chain transactions on the blockchain and have them visualized on a google map in real time. Use chainpoint proofs to prove that a particular item/product was at a location at a given point in time. (GrowNYC, Chainpoint)

Biggest problems:
Traceability - being able to answer questions such as where did this case of strawberries come from.
Manual work - a lot of manual effort is spent recording and piecing together history for particular items.

Use the Tierion/Chainpoint API to perform delivery validation. I should be able to query on a particular item and get a linked list of that items history that is validated on Tierion and the BTC blockchain.

### API

Record instance of item(s), equivalent to a packing slip or farmers label of an item.
<pre>
POST /api/items/add
[
    {
        "name": "Swiss Chard/Green", // name of the item (not necessarily unique)
        "unit": "12 BU", // quantity or size of the item
        "metadata": "Product of USA", // additional comments or info on this item
        "uuid": XXXX, // uuid of the item (string)
        "origin": Satur Farms NY 11935"
        "packDate": "05-08-2018"
    },
    ...
]
</pre>

Record deliveries of item(s)
<pre>
POST /api/deliveries/add
[
    {
        "itemId": XXXX, // uuid of the received item. (id)
        "locationId": XXXXX, // uuid of the receiving location (id)
        "lat": XXXX, // latitude of the receiver (float)
        "lng": XXX // longitude of the receiver (float)
        "timeMs": XXXXX // time of delivery (time ms)
    },
    ...
]
</pre>


Get the history of an item
<pre>
GET /api/item/history
{
    "itemId": XXXX // uuid of the desired item (id)
}
</pre>

Return all registered deliveries
<pre>
GET /api/deliveries
</pre>


Return all registered items
<pre>
GET /api/items
</pre>

### Structure

<ul>
<li><b>/server</b>: Server and api for submitting scheduling data.</li>
<li><b>/client</b>: Client side reactjs website</li>
<li><b>/screenshots</b>: Screenshots of app</b></li>  
</ul>

### Screenshots

<div width="400" style="text-align:center">
    <h3>AnchorSupply Home Page</h3>
        <img src="./screenshots/home_page.png" width="600" style="margin: 0 auto"/>
    <h3>Detailed Routing (Expanded View)</h3>
        <img src="./screenshots/iphone.png" width="600" style="margin: 0 auto"/>
    <h3>API Documentation</h3>
        <img src="./screenshots/api.png" width="600" style="margin: 0 auto"/>
    <h3>Proof of Delivery</h3>
        <img src="./screenshots/routing_2.png" width="600" style="margin: 0 auto"/>
</div>

### TODO:

* Create Logo. X
* Create API documentation. Understand the api interfaces and json body formats. X
* Create basic marketing website UI design / or use framework that allows plugging in an API doc page. X
* Add tests to server code.
* Check items table for duplicates.

### Dev Notes
<b>Check the `README.md` files in each subproject for how to start services.</b>