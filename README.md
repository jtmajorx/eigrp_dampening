This Script is to add per-peer EIGRP dampening capabilites to EIGRP. While interface dampening exists, this script
can dampen a peer based on adj flaps inwhich the interface remains up/up. The current timers of the script will 
begin dampening after (3) flaps within 60 seconds. The neighbor is restored after 120 seconds. However these values are
easily configurable.



event manager applet EIGRP-DAMPEN
	trigger occurs 3 period 60 ### Controls number of flaps within period of time before event is triggered.
 
event manager applet EIGRP-UNDAMPEN
	event none maxrun 180 ### Max-run time of the EEM applet, needs to be higher than trigger delay.
	trigger delay 120 ### Adjusts how long peer is dampened
