# fuse74-s2i-deployment

```
$ oc new-app fuse7-java-openshift:1.4~https://github.com/abouchama/fuse74-s2i-deployment.git --name=custom-fuse74-s2i-openshift
--> Found image ad4d6e5 (4 months old) in image stream "fuse74/fuse7-java-openshift" under tag "1.4" for "fuse7-java-openshift:1.4"

    Fuse for OpenShift
    ------------------
    Build and run Spring Boot-based integration applications

    Tags: builder, java, fuse

    * A source build using source code from https://github.com/abouchama/fuse74-s2i-deployment.git will be created
      * The resulting image will be pushed to image stream tag "custom-fuse74-s2i-openshift:latest"
      * Use 'oc start-build' to trigger a new build
    * This image will be deployed in deployment config "custom-fuse74-s2i-openshift"
    * Ports 8778/tcp, 9779/tcp will be load balanced by service "custom-fuse74-s2i-openshift"
      * Other containers can access this service through the hostname "custom-fuse74-s2i-openshift"

--> Creating resources ...
    imagestream.image.openshift.io "custom-fuse74-s2i-openshift" created
    buildconfig.build.openshift.io "custom-fuse74-s2i-openshift" created
    deploymentconfig.apps.openshift.io "custom-fuse74-s2i-openshift" created
    service "custom-fuse74-s2i-openshift" created
--> Success
    Build scheduled, use 'oc logs -f bc/custom-fuse74-s2i-openshift' to track its progress.
    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
     'oc expose svc/custom-fuse74-s2i-openshift'
    Run 'oc status' to view your app.
    
```
  
```
$ oc logs -f bc/custom-fuse74-s2i-openshift                    
Cloning "https://github.com/abouchama/fuse74-s2i-deployment.git" ...
	Commit:	f817d4e92b83c143672d4b4a4b2e55540feffc47 (Update README.md)
	Author:	Abdellatif BOUCHAMA <abdellatif.bouchama@gmail.com>
	Date:	Mon Jan 13 15:30:18 2020 +0100
Using docker-registry.default.svc:5000/fuse74/fuse7-java-openshift@sha256:5555a6031cbb8eb09cfeb73cacaabefd5a5824637b047af69b981bc66bdd8b3c as the s2i builder image
==================================================================
Starting S2I Java Build .....
S2I source build with plain binaries detected
Copying binaries from /tmp/src to /deployments ...
Checking for fat jar archive...
... done

Pushing image docker-registry.default.svc:5000/fuse74/custom-fuse74-s2i-openshift:latest ...
Pushed 0/6 layers, 2% complete
Pushed 1/6 layers, 17% complete
Push successful
```
