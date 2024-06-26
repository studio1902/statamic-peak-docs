# Protections

Peak has two protections in place that prevent clients from:

1. Deleting pages that have a collection mounted on them: `App/Listeners/PreventDeletingMounts.php`.
2. Editing Super Admin users as a non Super Admin user: `App/Policies/CustomUserPolicy.php`.
