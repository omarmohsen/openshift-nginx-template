
# openshift-nginx-template
OpenShift nginx template, the template uses RPM based docker images as well as config maps instead of building docker images with new configuration each time

## Usage
In order to use the template use the following oc command:

    oc process -f nginx-template.yaml NGINX_ROUTE_HOSTNAME=<nginx route hostname without http> | oc create -f -


After modifying the nginx.conf file inside the config map you need to let nginx load the new configuration, either to you can restart the container or can execute the following command inside the container without restarting:

    nginx -s reload


