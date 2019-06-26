---
id: api-calls-postman
order: 1
title: API calls via Postman
category: 3. Using the Centrifuge Node
---

Once the Centrifuge node is up and running you are able to start submitting invoices and tokenize these documents via simple API calls. For this, you can either use Postman (see [Recommended tools](/docs/getting-started/tools) or use your standard command-line interface. If you use Postman, make sure you have imported the most recent [Centrifuge Postman Collection](https://www.getpostman.com/collections/778e9c17a9fc7c5c57af).

## Before you start 
Confirm that your Centrifuge Node is up und running, for example with a PING (See section [Post install verification](/docs/getting-started/ping)). If it is not running, run the Centrifuge Node using the `config.yaml` file you created:

  ```bash
  $ centrifuge run -c /<PATH-TO-CONFIG-DIR>/config.yaml
  ```

where `PATH-TO-CONFIG-DIR` is your location of the `config.yaml`.

Open the Postman Desktop App and select the calls you want to make. You find more information on these calls here: [Node API](https://centrifuge-os-node-api-1.api-docs.io/0.0.5/). 

Please find examples for exchanging invoices and minting business NFTs below: 

## Create an invoice

To create an invoice use the POST call under the menu item _invoice_. Always make sure to add your Centrifuge ID under **Header** > **authorization**. Then go to **Body** and fill in the document template accordingly. Press send to create the invoice.

**Header:**
![CreateInvoiceHeader](https://imgur.com/MjwRrTC.png)


**Body:**
![CreateInvoiceBody](https://i.imgur.com/OwoLreB.png)

Creating an invoice automatically generates a document ID for the said invoice. This is required for the recepient to receive the invoice or if you want to update an invoice. 

## Receive an invoice

The recipient is able to look up the specific invoice by calling GET under the menu item _invoice_. The recipient will need the document ID and add it to the call, e.g: `http://localhost:8082/v1/invoices/<Add DocumentID>`. Then press send. The invoice details will be shown in the **Body** below.
  
![ReceiveInvoice](https://i.imgur.com/CcCtrBX.png)

## Update an invoice

Use the PUT command under the menu item _invoice_ to update an invoice. Add the document ID to the call as explained above. Then press send and update accordingly.

![Update Invoice](https://i.imgur.com/70q6ivs.png)


## Mint business NFTs
To mint a business NFT use the POST command under the menu item _token_. First add your Centrifuge ID under **Header** > **authorization**. Then select **Body** and fill in the document template. Keep in mind that you want to use a deposit address where you are able to move the NFT later on.

![Mint Invoice](https://i.imgur.com/55A5vLl.png)

## Verify Job Done
After each job you receive an output that contains a job ID. You can use this job ID to check whether the job was successfull. Go to the menu item _jobs_ in your Postman Centrifuge collection and call GET. Do not forget to add your Centrifuge ID as authorization value and state the job ID in the GET call. 

![Job Status](https://i.imgur.com/eqlggeU.png)
