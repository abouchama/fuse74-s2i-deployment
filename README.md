# fuse74-s2i-deployment

```
$ oc new-app fuse7-java-openshift:1.4~https://github.com/abouchama/fuse74-s2i-deployment.git --name=custom-fuse74-s2i-openshift
--> Found image ad4d6e5 (4 months old) in image stream "fuse74/fuse7-java-openshift" under tag "1.4" for "fuse7-java-openshift:1.4"

    Fuse for OpenShift
    ------------------
    Build and run Spring Boot-based integration applications

    Tags: builder, java, fuse

    * A source build using source code from https://github.com/abouchama/fuse-s2i.git will be created
      * The resulting image will be pushed to image stream tag "custom-fuse-74-s2i-openshift:latest"
      * Use 'oc start-build' to trigger a new build

--> Creating resources with label build=custom-fuse-74-s2i-openshift ...
    imagestream.image.openshift.io "custom-fuse-74-s2i-openshift" created
    buildconfig.build.openshift.io "custom-fuse-74-s2i-openshift" created
--> Success
```


```
$ oc logs -f bc/custom-fuse-74-s2i-openshift                     
Cloning "https://github.com/abouchama/fuse-s2i.git" ...
	Commit:	984f71461c59e6d43f29140beb0bdcfbd9345980 (Update assemble)
	Author:	Abdellatif BOUCHAMA <abdellatif.bouchama@gmail.com>
	Date:	Mon Mar 4 10:00:52 2019 +0100
Using docker-registry.default.svc:5000/fuse74/fuse7-java-openshift@sha256:5555a6031cbb8eb09cfeb73cacaabefd5a5824637b047af69b981bc66bdd8b3c as the s2i builder image
************************************************************************
* CUSTOM S2I FIS 2.0 (2.0) SPRING BOOT configured from an Openshift    *
************************************************************************
.... Copying RUN JAVA SHELL file from project ...
:: set uid & gid :: uid=1000140000 gid=0(root) groups=0(root),1000140000
uid=185(jboss) gid=0(root) groups=0(root),185(jboss)
ls -ltr /opt/run-java/run-java.sh
-rwxr-xr-x. 1 root root 18645 Sep  4 11:27 /opt/run-java/run-java.sh
sed -i '1000140000,0 s/^/#/' /opt/run-java/run-java.sh
sed: couldn't open temporary file /opt/run-java/sedeeHYZB: Permission denied
/tmp/scripts/assemble: line 25: exec_args: command not found
/tmp/scripts/assemble: line 25: java_options: command not found
/tmp/scripts/assemble: line 25: classpath: command not found
#sed -i '1000140000irun_fuse=exec java -cp ' /opt/run-java/run-java.sh
sed: couldn't open temporary file /opt/run-java/sedEw6X6z: Permission denied
sed -i '0i eval ' /opt/run-java/run-java.sh
sed: -e expression #1, char 2: invalid usage of line address 0
==================================================================
Starting S2I Java Build .....
S2I binary build from fabric8-maven-plugin detected
Copying binaries from /tmp/src/maven to /deployments ...
... done

Pushing image docker-registry.default.svc:5000/fuse74/custom-fuse-74-s2i-openshift:latest ...
Pushed 1/6 layers, 17% complete
Push successful
```

