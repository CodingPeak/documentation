
.. code-block:: bash

    curl -s --user 'api:YOUR_API_KEY' -G \
	https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/campaigns

.. code-block:: java

 import com.mashape.unirest.http.HttpResponse;
 import com.mashape.unirest.http.JsonNode;
 import com.mashape.unirest.http.Unirest;
 import com.mashape.unirest.http.exceptions.UnirestException;
 
 public class MGSample {
 
     // ...
 
     public static JsonNode getCampaigns() throws UnirestException {
 
         HttpResponse<JsonNode> request =  Unirest.get("https://api.mailgun.net/v3/" + YOUR_DOMAIN_NAME + "/campaigns")
             .basicAuth("api", API_KEY)
             .queryString("limit", 2)
             .asJson();
 
         return request.getBody();
     }
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('YOUR_API_KEY');
  $domain = 'YOUR_DOMAIN_NAME';

  # Issue the call to the client.
  $result = $mgClient->get("$domain/campaigns", array(
      'limit' => 5,
      'skip' => 5
  ));

.. code-block:: py

 def get_campaigns():
     return requests.get(
         "https://api.mailgun.net/v3/YOUR_DOMAIN_NAME/campaigns",
         auth=('api', 'YOUR_API_KEY'))

.. code-block:: rb

 def get_campaigns
   RestClient.get("https://api:YOUR_API_KEY"\
                  "@api.mailgun.net/v3/YOUR_DOMAIN_NAME/campaigns")
 end

.. code-block:: csharp

 using System;
 using System.IO;
 using RestSharp;
 using RestSharp.Authenticators;

 public class GetCampaignsChunk
 {

     public static void Main (string[] args)
     {
         Console.WriteLine (GetCampaigns ().Content.ToString ());
     }

     public static IRestResponse GetCampaigns ()
     {
         RestClient client = new RestClient ();
         client.BaseUrl = new Uri ("https://api.mailgun.net/v3");
         client.Authenticator =
             new HttpBasicAuthenticator ("api",
                                         "YOUR_API_KEY");
         RestRequest request = new RestRequest ();
         request.AddParameter ("domain", "YOUR_DOMAIN_NAME", ParameterType.UrlSegment);
         request.Resource = "{domain}/campaigns";
         request.AddParameter ("limit", 2);
         return client.Execute (request);
     }

 }

.. code-block:: go

 // Not supported

.. code-block:: js

 var DOMAIN = 'YOUR_DOMAIN_NAME';
 var mailgun = require('mailgun-js')({ apiKey: "YOUR_API_KEY", domain: DOMAIN });

 mailgun.get(`/${DOMAIN}/campaigns`, function (error, body) {
   console.log(body);
 });
