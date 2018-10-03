## SUBSCRIPTION MANAGEMENT ON REHL SYSTEMS

<br>

1. Register the system using the following command:

	`subscription-manager register --name=NAME_WANTED_ON_RHSM_PORTAL`


	If the `--name` option is not used then the system hostname is used but it should not be used when the newly installed system has the localhost.localdomain as its FQDN.


2. List the available subscriptions using the following command:

	2.1	For that particular system:

		`subscription-manager list --available`

	2.2	All the subscriptions:

		`subscription-manager list --available --all`


3. Copy the pool id of the required subscription that you want to attach.


4. Attach the subscription using the following command:

	`subscription-manager attach --pool=POOL_ID`


5. Verify the list of attached subscriptions using the following command:

	`subscription-manager list --consumed`


6. Now the system is registered and subscribed to proper update channels.

7. In case of any mistake do not just run `subscription-manager clean` rather first remove the attached subscriptions so you don't leave the RHSM portal with stale information.

	7.1. To remove a particular subscription:

    `subscription-manager remove --pool=POOL_ID`

	7.2. To remove all the attached subscriptions:

    `subscription-manager remove --all`


8. Unregister the system from RHSM portal to remove its entry from RHSM portal and repeat the process with right options.

	To unregister the system use the following command:

    `subscription manager unregister`


9. For any help use the following commands:

	9.1. Use the installed man documentation using the following command:

    `man subscription-manager`

	9.2. Run subscription-manager without any options to see the usage foramt:

	`subscription-manager`

	9.3. See action specific help using the following command:

	` subscription-manager [register | clean | unregister | etc] --help`



10. For a quick registration process use the auto attach functionality:

	`subscription-manager register --name=NAME_WANTED_ON_RHSM_PORTAL --auto-attach`
