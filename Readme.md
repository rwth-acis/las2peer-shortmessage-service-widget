![las2peer](https://raw.githubusercontent.com/rwth-acis/las2peer/master/img/logo/bitmap/las2peer-logo-128x128.png)

las2peer-shortmessage-service-widget
====================================

This is a [Polymer](https://www.polymer-project.org/1.0/) widget for the [las2peer ShortMessage-Service](https://github.com/rwth-acis/las2peer-ShortMessage-Service).
It can be used in many use cases and even more frontends to provide a chat messaging functionality.
Please take a look at the examples section below for usage examples.

Requirements
------------

* [bower](https://bower.io/)
* [polyserve](https://www.npmjs.com/package/polyserve)

Installation
------------

Install requirements:

    sudo apt-get install npm
    sudo ln -s /usr/bin/nodejs /usr/bin/node

    sudo npm install -g bower polyserve

To use the widget in your project just install itself with:

    bower install --save https://github.com/rwth-acis/las2peer-shortmessage-service-widget.git#v0.1.0

Alternatively you can add the entry manually to your **bower.json** file and call `bower install` afterwards.

    {
         "dependencies": {
             ...
             "las2peer-shortmessage-service-widget": "git@github.com:rwth-acis/las2peer-shortmessage-service-widget.git#v0.1.0"
             ...
         }
    }

Standalone Demo & Test
----------------------

Fetch and install dependencies for the widget with the following command in the root folder:

    bower install

Start the polyserve instance:

    polyserve

Look at the console output for the documentation and demo URL.

Usage-Examples
--------------

Don't forget to include the import in the **<head>** tag of your website, like:

    <head>
        ...
        <link rel="import" href="../las2peer-shortmessage-service-widget.html">
        ...
    </head>

Example 1: Simple chat window for *User A* to chat with *User B* (represented by agent id 123456789)

    <las2peer-shortmessage-service-widget base-url="https://my-webconnector-endpoint.example.org" login-name="User A" login-password="userAPassword" recipient-id="123456789" ></las2peer-shortmessage-service-widget>

Example 2: You can also assign the sender and recipient dynamically using Javascript. (like the demo)

    <las2peer-shortmessage-service-widget id="smsWidget" base-url="https://my-webconnector-endpoint.example.org"></las2peer-shortmessage-service-widget>
    ...
    <script>
        var smsWidget = document.getElementById("smsWidget");
        
        function setUser() {
          smsWidget.setAttribute("login-name", {some user login name});
          smsWidget.setAttribute("login-password", {some user password});
          smsWidget.clearMessages(); // reset the widget
        }
        
        function setRecipient() {
          smsWidget.setAttribute("recipient-id", {some recipient user agent id});
          smsWidget.clearMessages(); // reset the widget
        }
        
        // wait for all components before applying any settings
        window.addEventListener("WebComponentsReady", function() {
          setUser();
          setRecipient();
        });
    </script>

For more details about attributes, member functions and manipulation options, please look at the documentation URL provided by polyserve or comments in the **las2peer-shortmessage-service-widget.html** file.
