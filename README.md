# How-to Setup AEM As A Service on Linux
Details on how-to setup AEM as a Service on Linux. Used CentOS 7 as an example.

## Pre-requisites
1. AEM Installed on your server. Copy the path of the install (e.g: /mnt/crx)
2. Start AEM (e.g `java -jar cq-quickstart-author-p4502.jar`) once. This will generate all the necessary folders, especially **/mnt/crx/crx-quickstart/bin** that is required by the scripts.
2. Create a user who will have access to the service. (e.g: aem)

## Step-by-step guide
1. You will need root access 
2. Download these 2 files
   * aem
   * aem.service
3. Open `aem` script file and update the below
   * AEM_ROT (e.g: `/mnt/crx` is the root, where `/mnt/crx/crx-quickstart` is the full path)
   * AEM_USER (e.g: `aem`) 
4. SCP these files to the server
   * Copy `aem` to `/usr/bin/aem`
     * Example: From terminal on your desktop `$ scp <filename> user@1.1.1.1:/usr/bin/aem`
   * Copy `aem.service` to `/etc/system.d/system/aem.system`
     * Example: From terminal on your desktop `$ scp <filename> user@1.1.1.1:/etc/system.d/system/aem.system`
5. SSH to your server
   * `ssh user@1.1.1.1`
6. Give permissions to the files
   * `sudo chmod u+rwx /usr/bin/aem`
   * `sudo chmod u+rwx /etc/system.d/system/aem.system`
7. Update 
   * `cd /etc/system.d/system`
   * `systemctl enable aem.system`
8. You can restart the server or run the below commands to start AEM. Make sure you run **Pre-requisite Step 2** before running this command.

## Commands to START, RESTART and STOP AEM
1. Start AEM - `sudo service aem start`
2. Restart AEM - `sudo service aem restart`
3. Stop AEM - `sudo service aem stop`

## Notes
1. The example above was tested on CentOS 7
2. AEM 6.3 version was used. Although the above process should work for AEM 6.x