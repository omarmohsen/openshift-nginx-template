
# openshift-nginx-template
OpenShift nginx template, the template uses RPM based docker images as well as config maps instead of building docker images with new configuration each time

## Usage
In order to use the template use the following oc command:

    oc process -f nginx-template.yaml NGINX_ROUTE_HOSTNAME=<nginx route hostname without http> | oc create -f -


After modifying the nginx.conf file inside the config map you need to let nginx load the new configuration, either to you can restart the container or can execute the following command inside the container without restarting:

    nginx -s reload

## Other Parameters:

**NGINX_VERSION:**
"Specify the nginx version you are using, valid options are: nginx-112, nginx-110, nginx-18, nginx-16" 

**NGINX_BASE_IMAGE_OS:**
"RPM-based distros are used in this template, either use rhel7 or centos7, note: if you are using RHEL 7 you must have a valid subscription"

**NGINX_DEFAULT_HTTP_PORT:**
"Default port nginx uses to listen on, if you specify a port lower than 1024, the container must run as privileged"

**NGINX_ACCESS_LOG_PATH:**
Path where nginx should write the access logs, either specify the file or if you want it the logs to be printed in the container logs redirect it to STDOUT by entering the value /dev/stdout"

**NGINX_ERROR_LOG_PATH:**
"Path where nginx should write the error logs, either specify the file or if you want it the logs to be printed in the container logs use /dev/stdout"


