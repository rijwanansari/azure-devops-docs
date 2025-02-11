---
title: Shelvesets Command
titleSuffix: Azure Repos
description: Shelvesets Command
ms.assetid: 731a4339-1ba7-45ab-a551-51c3f4ae158c
ms.technology: devops-code-tfvc
ms.topic: reference
ms.date: 07/13/2022
monikerRange: '<= azure-devops'
---


# Shelvesets command (Team Foundation Version Control)

[!INCLUDE [version-lt-eq-azure-devops](../../includes/version-lt-eq-azure-devops.md)]
[!INCLUDE [version-vs-gt-2013](../../includes/version-vs-gt-2013.md)]


The **shelvesets** command displays information about a set of shelved changes.

## Prerequisites

To use the **shelvesets** command, you must the have **Read** permission and the **Check out** permission set to **Allow** for the items in the shelvesets.  For more information, see  [Default TFVC permissions](../../organizations/security/default-tfvc-permissions.md).

## Syntax

```
tf shelvesets [/owner:ownername] [/format:(brief|detailed)] [/collection:TeamProjectCollectionUrl]] [/login:username,[password]] shelvesetname
```

## Parameters

### Argument

|**Argument**|**Description**|
|---|---|
|*ownername*|Provides a value such as * or DOMAIN\john to the **/owner** option.|
|*shelvesetname*|The name of the shelveset.|
|*TeamProjectCollectionUrl*|The URL of the project collection that contains a set of shelved changes about which you want to display information (for example, http://myserver:8080/tfs/DefaultCollection).|
|*username*|Provides a value to the **/login** option. You can specify a username value as either *DOMAIN*\*UserName* or *UserName*.|

### Option

|**Option**|**Description**|
|---|---|
|**/owner**|Specifies one or more shelveset owners. You can use wildcard characters.|
|**/format**|Specifies what kind of format to display shelveset information in.<br /><br />**Brief** displays the shelveset name, the name of the user who created it, and a shelveset comment, if one exists. **Detailed** displays the shelveset name, owner, and comment in addition to a list of associated work items and any check-in notes. **Brief** is the default value.|
|**/collection**|Specifies the project collection.|
|**/login**|Specifies the user name and password to authenticate the user with Azure DevOps.|

## Remarks

Shelvesets are created by the **shelve** command. Shelvesets are stored on the Team Foundation Server and can be retrieved into a workspace by any user who has sufficient permissions using the [Unshelve Command](unshelve-command.md). Unlike a changeset, a shelveset is a non-versioned entity. If you or another user unshelve the items of which a shelveset consists, edit several files, and re-shelve the shelveset, Team Foundation does not create a new version of the items for future comparison and maintains no record of who revised the items, when, or in what manner. For more information about deciding whether to shelve or check in a set of pending changes and a general overview of shelving, see [Working with Shelvesets](suspend-your-work-manage-your-shelvesets.md).

For detailed information about the individual source file revisions of which a particular shelveset consists, you can use the [Status Command](status-command.md) with the **/shelveset** option.

You can compare a shelved revision to its base shelveset version without unshelving the item into your workspace. You can use this feature to conduct a quick peer code review.

For more information on how to find the **tf** command-line utility, see [Use Team Foundation version control commands](use-team-foundation-version-control-commands.md).

### Examples

The following example displays information about the BuddyTest\_23 shelveset for the Team Foundation Server to which the current directory maps.

```
c:\projects>tf shelvesets BuddyTest_23
```

The following example lists the shelvesets owned by "John."

```
c:\projects>tf shelvesets /owner:John
```

The following example displays information about the shelvesets on the Team Foundation Server to which the current directory maps.

```
c:\projects>tf shelvesets /owner:*
```

## Related articles

- [Use Team Foundation version control commands](use-team-foundation-version-control-commands.md)
- [Status Command](status-command.md)
- [Changeset Command](changeset-command.md)
- [Shelve Command](shelve-command.md)
- [Unshelve Command](unshelve-command.md)
- [Working with Shelvesets](suspend-your-work-manage-your-shelvesets.md)
