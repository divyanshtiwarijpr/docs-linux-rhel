## Install *VMware Tools* in RHEL 6.

1. First resolve the dependencies that are required to enable all the functions using the following command: 

	`yum install binutils gcc make kernel-headers`

3. Mount the **VMware Tools** iso in the guest VM by select the VM and then clicking **VM** > **Install VMware Tools** in VMware Workstation Pro.

4. Extract the file contents in any directory:

	`mkdir /PATH_TO_EXTRACTION_FOLDER`
	
	`tar -xvf /PATH_TO_ISO -C /PATH_TO_EXTRACTION_FOLDER`
	
	`chmod +x /PATH_TO_EXTRACTION_FOLDER`

5. Run the installation script as root user.

6. Run `vmware-user` or logout and login again or restart the X server.

7. If in case of any error run the `vmware-uninstall-tools.pl` script and reinstall using forced certificate generation option.

8. Check the installation after configuring shared folders and running `vmware-hgfsclient` and then checking the `/mnt/hgfs/SHARE_NAME` folder. 

10. If the share is not created before installation then mounting of hgfs shares may fail.




