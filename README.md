# ose-custom-amq


1. Import the AMQ image
```
oc import-image my-jboss-amq-6/amq63-openshift --from=registry.access.redhat.com/jboss-amq-6/amq63-openshift --confirm -n openshift
```

2. Add the config file to the configuration directory and push to git
3. Create and start the s2i build
```
oc new-build openshift/amq63-openshift~https://github.com/noelo/ose-custom-amq.git
```

3. Create an amq app instance using an AMQ template, this will use the standard AMQ image
4. Edit the dc to change the image to the new custom AMQ image
```
e.g. image: 172.30.1.1:5000/custom-amq/ose-custom-amq
```
