---
title: NTFRS deprecation blocks promotion of replica DCs
description: NTFRS deprecation intentionally blocks the promotion of Windows Server 2016 RS3 replica DCs.
ms.date: 09/08/2020
author: delhan
ms.author: Delead-Han
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-server
localization_priority: medium
ms.reviewer: kaushika
ms.prod-support-area-path: Active Directory replication
ms.technology: ActiveDirectory 
---
# NTFRS deprecation intentionally blocks the installation of Windows Server version 1709 replica DCs

_Original product version:_ &nbsp; Windows Server 2016  
_Original KB number:_ &nbsp; 4023141

## Symptom

When you install a replica-domain controller that's running Windows Server version 1709 by using the [Install-ADDSDomainController](https://technet.microsoft.com/library/hh974723%28v=wps.630%29.aspx) cmdlet to a NTFRS-enabled domain, the installation fails, and you receive the following error message: The specified domain %1 is still using the File Replication Service (FRS) which is deprecated. This server does not support FRS and cannot be promoted as a replica into the specified domain. You should migrate the specified domain to use DFS Replication by using the DFSRMIG command before continuing. For more information, see https://go.microsoft.com/fwlink/?linkid=849270.
 Before Windows 10 version 1709 in installed, you receive the following message: The File Replication Service (FRS) is deprecated. To continue replicating the sysvol folder, you should migrate to DFS Replication by using the DFSRMIG command. If you continue to use FRS for sysvol replication in this domain, you might not be able to add domain controllers running a future version of Windows Server.
 Servers that indirectly run the Install-ADDSDomainController cmdlet in Server Manager are also affected. 

## Cause

This behavior is intended and by design and consistent with previous announcements about the deprecation of NTFRS in future versions of Windows. Windows Server 2016 is the initial release that ends support of NTFRS. 

## Resolution

Use the steps in the following article to migrate sysvol replication from FRS to DFSR:

[Sysvol replication Migration Guide: FRS to DFS replication](https://technet.microsoft.com/library/dd640019%28WS.10%29.aspx)