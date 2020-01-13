# fuse74-s2i-deployment

```
$ oc new-app fuse7-java-openshift:1.4~https://github.com/abouchama/fuse74-s2i-deployment.git --name=fuse74-s2i-2-openshift
--> Found image ad4d6e5 (4 months old) in image stream "fuse74/fuse7-java-openshift" under tag "1.4" for "fuse7-java-openshift:1.4"

    Fuse for OpenShift
    ------------------
    Build and run Spring Boot-based integration applications

    Tags: builder, java, fuse

    * A source build using source code from https://github.com/abouchama/fuse74-s2i-deployment.git will be created
      * The resulting image will be pushed to image stream tag "fuse74-s2i-2-openshift:latest"
      * Use 'oc start-build' to trigger a new build
    * This image will be deployed in deployment config "fuse74-s2i-2-openshift"
    * Ports 8778/tcp, 9779/tcp will be load balanced by service "fuse74-s2i-2-openshift"
      * Other containers can access this service through the hostname "fuse74-s2i-2-openshift"

--> Creating resources ...
    imagestream.image.openshift.io "fuse74-s2i-2-openshift" created
    buildconfig.build.openshift.io "fuse74-s2i-2-openshift" created
    deploymentconfig.apps.openshift.io "fuse74-s2i-2-openshift" created
    service "fuse74-s2i-2-openshift" created
--> Success
    Build scheduled, use 'oc logs -f bc/fuse74-s2i-2-openshift' to track its progress.
    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
     'oc expose svc/fuse74-s2i-2-openshift'
    Run 'oc status' to view your app.
```
  
```
$ stern fuse74-s2i-2                                           INT ✘  5m 37s  fuse74/openshift-abouchama-lab-pnq2-cee-redhat-com:443/quicklab/fuse74 ⎈  15:48:17
+ fuse74-s2i-2-openshift-1-build › git-clone
fuse74-s2i-2-openshift-1-build git-clone Cloning "https://github.com/abouchama/fuse74-s2i-deployment.git" ...
fuse74-s2i-2-openshift-1-build git-clone 	Commit:	3c5612f17a231f4c3f68020fea532907d5a577cf (Merge branch 'master' of https://github.com/abouchama/fuse74-s2i-deployment)
fuse74-s2i-2-openshift-1-build git-clone 	Author:	BOUCHAMA Abel <abdellatif.bouchama@gmail.com>
fuse74-s2i-2-openshift-1-build git-clone 	Date:	Mon Jan 13 15:47:31 2020 +0100
+ fuse74-s2i-2-openshift-1-build › manage-dockerfile
+ fuse74-s2i-2-openshift-1-build › sti-build
fuse74-s2i-2-openshift-1-build sti-build Using docker-registry.default.svc:5000/fuse74/fuse7-java-openshift@sha256:5555a6031cbb8eb09cfeb73cacaabefd5a5824637b047af69b981bc66bdd8b3c as the s2i builder image
fuse74-s2i-2-openshift-1-build sti-build ==================================================================
fuse74-s2i-2-openshift-1-build sti-build Starting S2I Java Build .....
fuse74-s2i-2-openshift-1-build sti-build S2I source build with plain binaries detected
fuse74-s2i-2-openshift-1-build sti-build Copying binaries from /tmp/src to /deployments ...
fuse74-s2i-2-openshift-1-build sti-build Checking for fat jar archive...
fuse74-s2i-2-openshift-1-build sti-build Found springboot-camel-fuse74-1.0-SNAPSHOT.jar...
fuse74-s2i-2-openshift-1-build sti-build ... done
fuse74-s2i-2-openshift-1-build sti-build
fuse74-s2i-2-openshift-1-build sti-build Pushing image docker-registry.default.svc:5000/fuse74/fuse74-s2i-2-openshift:latest ...
fuse74-s2i-2-openshift-1-build sti-build Pushed 0/6 layers, 1% complete
fuse74-s2i-2-openshift-1-build sti-build Pushed 1/6 layers, 17% complete
fuse74-s2i-2-openshift-1-build sti-build Push successful
+ fuse74-s2i-2-openshift-1-deploy › deployment
fuse74-s2i-2-openshift-1-deploy deployment --> Scaling fuse74-s2i-2-openshift-1 to 1
^[[A^[[Afuse74-s2i-2-openshift-1-deploy deployment --> Success
+ fuse74-s2i-2-openshift-1-b4nx5 › fuse74-s2i-2-openshift
^[[Dfuse74-s2i-2-openshift-1-b4nx5 fuse74-s2i-2-openshift Starting the Java application using /opt/run-java/run-java.sh ...
fuse74-s2i-2-openshift-1-b4nx5 fuse74-s2i-2-openshift exec java -javaagent:/opt/jolokia/jolokia.jar=config=/opt/jolokia/etc/jolokia.properties -javaagent:/opt/prometheus/jmx_prometheus_javaagent.jar=9779:/opt/prometheus/prometheus-config.yml -XX:+UseParallelGC -XX:GCTimeRatio=4 -XX:AdaptiveSizePolicyWeight=90 -XX:MinHeapFreeRatio=20 -XX:MaxHeapFreeRatio=40 -XX:+ExitOnOutOfMemoryError -cp . -jar /deployments/springboot-camel-fuse74-1.0-SNAPSHOT.jar
fuse74-s2i-2-openshift-1-b4nx5 fuse74-s2i-2-openshift OpenJDK 64-Bit Server VM warning: If the number of processors is expected to increase from one, then you should configure the number of parallel GC threads appropriately using -XX:ParallelGCThreads=N
- fuse74-s2i-2-openshift-1-deploy
fuse74-s2i-2-openshift-1-b4nx5 fuse74-s2i-2-openshift I> No access restrictor found, access to any MBean is allowed
fuse74-s2i-2-openshift-1-b4nx5 fuse74-s2i-2-openshift Jolokia: Agent started with URL https://10.129.0.24:8778/jolokia/
```
