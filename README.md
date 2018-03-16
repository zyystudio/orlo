# Orlo 

Orlo is about getting Pentaho Data Integration (PDI) on a diet to us it on small devices and edge processing 

We can:

* Remove OSGI, doing the following modifications:
	* The file classes/kettle-lifecycle-listeners removing or commenting listener entry for PdiOsgiBridge
	* The file classes/kettle-registry-extensions removing or commenting registry-extension entry for PdiOsgiBridge
	* Remove system/karaf/ folder 
* Remove from lib/ the following files:
	* blueprints*.jar
	* org.apache.aries.*.jar
	* org.apache.felix.*.jar
	* org.apache.karaf.*.jar
	* pdi-osgi-bridge-*.jar
	* pentaho-osgi-*.jar
* Chnage platform PentahoSystem.java and remove OSGI dependencies, compile and generate the pentaho-platform-core-8.0.jar file to replace the existing one in PDI
* Remove all unecessary plugins inside plugin/ folder, and we can allways get some back if required

As suggestted at: https://blog.twineworks.com/improving-startup-time-of-pentaho-data-integration-78d0803c559b
* Supply a host name explicitly by setting KETTLE_SYSTEM_HOSTNAME in ~/.kettle/kettle.properties.
* Modify your hosts file so your hostname is associated with 127.0.0.1. See jvm-takes-a-long-time-to-resolve-ip-address-for-localhost
* Ask the JVM to prefer ipv4 over ipv6, in case it is an ipv6 reverse lookup that takes a long time. You can do that by adding -Djava.net.preferIPv4Stack=true to the java options in kitchen.sh/bat or spoon.sh/bat. See https://docs.oracle.com/javase/8/docs/api/java/net/doc-files/net-properties.html