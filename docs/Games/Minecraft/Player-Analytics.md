## Plan | Player Analytics

[Video overview](https://www.youtube.com/watch?v=DvYh0MiZRks&t)

[Player Analytics](https://github.com/plan-player-analytics/Plan) is the ultimate server staff tool to monitor how
players are playing your server.  
A built-in web server displays insights into different aspects on the server such as Online activity, Player base and
how these change over time.

### Single server PlanA setup

To set planA up you will need a separate port added to your server and set the port setting to whatever you have
available that isn't currently being used.

!!! note 

    If you wish to connect through a custom domain you will need to have thiese settings.


| Name                   | Value                     | Description                                                                                                                                                                                                                            |
|------------------------|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Port                   | `8804` (use your port)    | Port of the Webserver                                                                                                                                                                                                                  |
| Alternative_IP         | `false`                   | Should an alternate address be used for the WebServer links                                                                                                                                                                            |
| Alternative_IP.Address | `your.domain.here:%port%` | Address to use as link in inspect and analyze commands if setting above is enabled. %port% will be replaced with the Port automatically. If you have port-forwarded an alternate address to the webserver port, %port% is not required |

