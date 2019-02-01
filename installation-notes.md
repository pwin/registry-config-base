1. Download snapshot of 2.0.0, at:

https://s3-eu-west-1.amazonaws.com/ukgovld/snapshot/com/github/ukgovld/registry-core/2.0.0-SNAPSHOT/registry-core-2.0.0-20190131.203500-25.war

2. Download registry-config-base master branch and copy the 
/ldregistry directory from there to /opt/ldregistry

3. Edit /opt/ldregistry/config/app.conf to set:

registry.baseUri     = http://localhost:8080/registry

4. Edit /opt/ldregistry/config/root-register.ttl to set

@base <http://localhost:8080/registry/> .

5. Ensure that:
     * /var/log/ldregistry
     * /var/opt/ldregistry
     * /var/opt/ldregistry/logstore 
     
exist, are empty and are accessible to the tomcat user

6. Copy the new snapshot war to tomcat webapps as registry.war (or whatever you want to call it)

7. Start tomcat

With that then go to http://localhost:8080/registry/ and confirm that it works.

If you try to then login it goes port 80 instead of 8080: 

http://localhost/registry/ui/login?return=http://localhost/registry/

But if you edit that URL:

http://localhost:8080/registry/ui/login?return=http://localhost:8080/registry/

then you can login with the password defined in the default user.ini
