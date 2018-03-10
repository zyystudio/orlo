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