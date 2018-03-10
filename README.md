# tiny-kettle

Tiny PDI for processing on IoT EDGE devices and to use in containers

Required:
- Remove all unecessary plugins
- Modify classes/kettle-lifecycle-listeners
	- Remove listener entry for PdiOsgiBridge
- Modify classes/kettle-registry-extensions
- Remove registry-extension entry for PdiOsgiBridge

Optional (for disk usage savings):
- Remove system/
- Remove from lib/ -
- blueprints*.jar
- org.apache.aries.*.jar
- org.apache.felix.*.jar
- org.apache.karaf.*.jar
- pdi-osgi-bridge-*.jar
- pentaho-osgi-*.jar

Compile PentahoSystem.java generate pentaho-platform-core-8.0.jar file and replace existing 