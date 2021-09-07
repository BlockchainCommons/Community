# Offboarding

The following processes should be used to offboard a volunteer, intern, or contractor who had been given permissions and is now leaving Blockchain Commons.

## GitHub Permissions

Check the list of outside collaborators, and remove as appropriate:

https://github.com/orgs/BlockchainCommons/outside-collaborators

Search the organization for uses of the person's GitHub ID and click on the "Code" tab:

1. Remove ID from any CODEOWNERS files.
2. Remove any active titles such as "Maintainer" in Credits of README, but maintain (and/or add) "Author", "Developer", or other credits showing historical role.
3. Obviously, do *not* touch the CLAs.

## Linode Permissions

Delete any user IDs created under Linode:

https://cloud.linode.com/account/users

Also:

1. Reset any passwords known by user. 
2. Remove any of user's public keys from `~/.ssh/id_rsa.pub` and/or `authorized_keys`. (This is the preferred way of giving access to users.)

