GRETA - Global Reference Engine Toolkit API
==========

####ENG
Greta (formerly knows as Nisci Docs) is a complete "framework" for description, production, consumption, and display of RESTful web services. The main goal of Greta is to distribute, to developers, the documentation for update at the same server rhythm.

We say goodbye to the building of complex pages that attempt to explain how to use our API… so often without success... or crumbling attempts to paste the server response into a green and black form and then groped vaguely describe how it works…

####ITA
Greta (alias Nisci Docs) è una specifica implementazione di un "framework" completo per la descrizione, produzione, consumo, e visualizzare di RESTful web services. L'obiettivo principale di Greta è quello di distribuire, a sistemi client e sviluppatori, la documentazione per aggiornare allo stesso ritmo del server.

Diciamo addio alla costruzione di complesse pagine online che tentano di spiegare come usare le nostre API..molto spesso senza riuscirci...o fatiscenti tentativi di incollare la risposta del server in un form verde e nero per poi tentare vagamente di descriverne il funzionamento.... 

How to Use It
-------------

### Download
You can use the Greta code AS-IS!  No need to build or recompile, just clone this repo and use the pre-built files in the `greta` folder.  If you like Greta as-is, stop here.

### Build
You can rebuild Greta on your own to tweak it or just so you can say you did. Just remember to tell me too! I am proud of you.

### Use
Once you uploaded entire folder, then open Greta, it will load the `Basic Docs Service` and show its APIs. In my case I included `sebeto API` i built for my University services and apps.
You can enter your own server url and click explore to view the API.

### Customize
You may choose to customize Greta UI for your organization. Here is an overview of whats in its various directories:

-    greta: Contains a distribution which you can deploy on a server or load from your local machine.
-    lib: Contains javascript dependencies which Greta depends on
-    node_modules: Contains node modules which Greta uses for its development.
-    do not forget that this project is based on [iodocs](https://github.com/mashery/iodocs) so it uses Javascript, JQuery and a lot of JS stuffs, the main interface is based on [Bootstrap](https://github.com/twitter/bootstrap) so…just customize it.

### Greta
To use Greta you should take a look at the source of Greta html page aka `Viewer.html` and customize it. This basically requires you to instantiate a niscidocsUi object and call load() on it as below:

```javascript
    window.niscidocsUi = new niscidocsUi({
				discoveryUrl:"sebeto.niscidocs",
                apiKey:"",
                dom_id:"niscidocs-ui-container",
                supportHeaderParams: false,
                headers: { "Authorization": "XXXX", "someOtherHeader": "YYYY" },
                supportedSubmitMethods: ['get', 'post', 'put']
            });
            window.niscidocsUi.load();
        });
```

* *discoveryUrl* parameter should point to a resource listing url as per `sebeto.niscidocs`
* *dom_id parameter* is the the id of a dom element, usually a `div` element inside which Greta will put the user interface for Greta
* *booleanValues* Greta renders boolean data types as a dropdown. By default it provides a 'true' and 'false' string as the possible choices. You can use this parameter to change the values in dropdown to be something else, for example 0 and 1 by setting booleanValues to new Array(0, 1)
* *docExpansion* controls how the API listing is displayed. It can be set to 'none' (default), 'list' (shows operations for each resource), or 'full' (fully expanded: shows operations and their details)
* *onComplete* is a callback function parameter which can be passed to be notified of when Greta has completed rendering successfully.
* *onFailure* is a callback function parameter which can be passed to be notified of when Greta encountered a failure was unable to render.
* All other parameters are explained in greater detail below


### HTTP Methods and API Invocation
Greta supports invocation of all HTTP methods APIs but only GET methods APIs are enabled by default. You can choose to enable other HTTP methods like POST, PUT and DELETE. This can be enabled by setting the supportedSubmitMethods parameter when creating Greta instance.

For example if you wanted to enable GET, POST and PUT but not for DELETE, you'd set this as:

    supportedSubmitMethods: ['get', 'post', 'put']

_Note that for POST/PUT body, you'd need to paste in the request data in an appropriate format which your service can handle_

### Header Parameters
header parameters are supported. However because of [Cross-Origin Resource Sharing](http://www.w3.org/TR/cors/) restrictions, Greta, by default, does not send header parameters. This can be enabled by setting the supportHeaderParams to true when creating Greta instance as below:

    supportHeaderParams: true

### Custom Header Parameters - (For Basic auth etc)
If you have some header parameters which you need to send with every request, use the headers as below:

     headers: { "Authorization": "XXXX", "someOtherHeader": "YYYY" }

### Api Key Parameter
If you enter an api key in Greta, it sends a parameter named 'api\_key' as a query (or as a header param if you've enabled it as described above). You may not want to use the name 'api\_key' as the name of this parameter. You can change its name by setting the _apiKeyName_ parameter when you instantiate a Greta instance. For example to call it 'sessionkey'

    apiKeyName: "sessionkey"

How to Improve It
-----------------

Create your own fork of [fabiosoft/Greta](https://github.com/fabiosoft/Greta)

To share your changes, [submit a pull request](https://github.com/fabiosoft/Greta/pull/new/master).

License
-------

Copyright 2012-2013 CC BY-NC-SA 3.0 IT

[![Licenza Creative Commons](http://i.creativecommons.org/l/by-nc-sa/3.0/it/88x31.png)](http://creativecommons.org/licenses/by-nc-sa/3.0/it/)

Quest'opera è distribuita con Licenza [Creative Commons Attribuzione - Non commerciale - Condividi allo stesso modo 3.0 Italia](http://creativecommons.org/licenses/by-nc-sa/3.0/it/).

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
