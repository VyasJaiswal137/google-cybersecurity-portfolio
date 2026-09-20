
# Activity 3: Elevated Privileges and System User Administration

## Scenario & Objective

This activity centered on managing user accounts, system groups, and administrative permissions. The objective was to carry out user administration tasks safely while enforcing key security principles, such as avoiding continuous root logins and controlling access rights.

## Commands Used

`sudo`, `useradd`, `usermod`, `userdel`

## Key Tasks Completed

### Privilege Escalation Management

* Executed administrative commands with elevated privileges using `sudo`, ensuring system changes were made securely without directly logging in as the root user.

### User Account Provisioning

* Provisioned new user accounts on the system using `sudo useradd`.
* Configured primary group assignments using the `-g` option and assigned supplemental group permissions using the `-G` option during initial account creation.

### Account Modification & Group Assignment

* Updated attributes and group access for existing user accounts using `usermod`.
* Safely appended supplemental groups to existing users using the `-a -G` options together, preventing existing group memberships from being accidentally overwritten.

### Account Decommissioning

* Safely removed user accounts from the system using `sudo userdel` when access was no longer required.
