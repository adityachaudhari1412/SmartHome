# SmartHome



This repository includes the source code of the smarthome-verification project. This is a work-in-progress repository.
The code currently includes the impementation of a smart home architecture and three case studies (smart systems).
A smart home is modelled to consist of three types of devices: controllers, sensors and dumb-devices. Sensors measure different values and controllers control
dumb-devices depending on those sensor values. The sensor-controller dependency is captured using an observer pattern.
Currently, three smart systems work: upon launching the application, the devices display a message indicating the action they execute.
The verification of the smart systems is done by static program analysis for which we developed a checker on top of Google's error-prone framework as
one of the bugpatterns. The checker checks whether the code of the controllers satisfies a set of dependency policies which are reprensented as first order
formulae A dependency policy states the sensor conditions under which
a controller can send a command to a dumb-device.





To build and launch the application with the checker enabled, execute the build.xml script by simply typing:
ant
in a terminal (if you want to compile the checker on your own, you need to install error-prone and to save you from all that, we already provide a jar file for our static analysis tool).
You should see errors indicating potential security vulnerabilities in the code of the controllers. 


We also provide a jar which you can execute (see command below) to see the smart home simulation running.
Note that the jar is created only if the project compiles correctly.
To see the static analysis at work, we developed several Evil Controllers which are
detected at compile time thereby making the compilation fail (with the above log output). If you want to build the project yourself,
you may comment out the
evil controller instantiation lines from Platform.java to complete the compilation successfully. After that, you can create the jar file
for the project yourself by typing ant jar which can be executed by typing:
java -jar target/jar/${projectname}.jar
