setenv.bat
For Linux, MacOS, etc, remove "set " from beginning of the line.

~~~
set CATALINA_OPTS=-Dcom.sun.management.jmxremote.port=%my.jmx.port%
  -Dcom.sun.management.jmxremote.rmi.port=%my.rmi.port%
  -Dcom.sun.management.jmxremote.ssl=false
  -Dcom.sun.management.jmxremote.authenticate=false
~~~

