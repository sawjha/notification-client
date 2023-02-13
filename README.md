Connection-less Client:

    Run the command:
    java -jar epnm-restconf-nbi-notifications-connection-less-client.jar <HOST_IP_ADDRESS> <PORT_NUMBER>
        -Example: java -jar epnm-restconf-nbi-notifications-connection-less-client.jar 10.155.124.44 7080
            -where 10.155.124.44 is the IP address that you want to subscribe to on port 7080
        
    From there, you may subscribe to notifications on an EPNM server by posting to:
    https://<EPNM_SERVER>/restconf/data/v1/cisco-notifications:subscription/
    with the following payload:
        {
            "push.endpoint-url":"http://<CLIENT_IP_ADDRESS>:<CLIENT_PORT>/notifications",
            "push.topic":"inventory",
            "push.format": "json"
        }

    So for the example above, you would subscribe with the following payload:
        {
            "push.endpoint-url":"http://10.155.124.44:7080/notifications",
            "push.topic":"inventory",
            "push.format": "json"
        }



-------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------


Connection-Oriented Client(Using websockets)

    Run the command as admin(must be ran as admin):
        java -jar epnm-restconf-nbi-notifications-connection-oriented-client.jar 
            -answer the prompts by pressing enter/return key after typing the answer:
                -Use the EPNM Server's fully qualified domain name instead of IP address
                -provide user/pass
                -Select the number for the topic you wish to subscribe to (Ex. Type “1” and press enter for inventory)
		 -Select the number for the format you want.
		 -providing filters must follow the format FILTER_TYPE=FILTERVALUE without quotes (spaces are ok)
			Ex: category=System&severity=!minor


	     -Once you press enter, if the credentials are correct and filters are valid, you should see a prompt saying
		“Listening for notifications”


    
