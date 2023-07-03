# MRE: 2GP Profile Filtering

> `sfdx package version create` removes `fieldPermissions` too aggressively

## Issue description

`<fieldPermissions>` for `Event` and `Task` are being removed from Profiles.

## Reproduction

Create an Unlocked Package first:

```console
sfdx package create -t Unlocked --no-namespace --org-dependent --path force-app -n "2GP Profile Filtering"
```

Now create a package version:

```console
export SF_LOG_LEVEL="debug"
sfdx package version create -p force-app
```

See output in `~/.sf/sf.log`:

```text
The profile "Dummy Profile" from the "/path/to/project/force-app/main/default/profiles/Dummy Profile.profile-meta.xml" directory was added to this package version.
  The "Event.Event_Field__c" profile setting was removed from the "Dummy Profile" profile.
  The "Task.Task_Field__c" profile setting was removed from the "Dummy Profile" profile.
```
