# easee_load_balancing

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdala318%2Feasee_load_balancing%2Fblob%2Fmain%2Feasee_load_balancing.yaml" target="_blank"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a><br><br><br>
Blueprint for load balancing on Easee

## Automation setup an explaination

Once blueprint is installed it's time to setup the automation.

1. Identify your Easee charger entitiy for charger state.
2. Identify your Easee charger entitiy for charger dynamic_circuit_limit.
    * Make sure you pich the **circuit** limit since that one has access to all 3 phases (the charger limit only one single).
    * This entity might be disable by default, if so go to the Easee device in HomeAssistant, click show all entities, open the settings for this entity and enable it (wait until it shows up with values).
3. Identify the house mains currents entities for ewach phase.
    * Here you need to make sure you match the mains current phase to those that are connected to each Easee charger phase, they don't necessary have to be 1-to-1, 2-to-2 etc. You may have to twinkle around a bit to figure this out.
    * A way to identify how the phases are connected may be to manually force the charget to single phase charging (call Easee service to set dynamic circuit limit to like 10A on one phase and 0A on the others, it your charger is configured to automatic phase selection it should then switch to single phase charging on the one phase that is above 6A and that phase should show increased current on the mains current sensor).
4. Set the configuration max limit to keep main current below. Should likely be at or slightly below your mains fuse capacity
5. Set the configuration max limit for charger. This current is already limited by your chargers static limit and only makes sense to limit further if you have a need to do so. If not, just set it to the max value.
6. Save and monitor the bahavior!
