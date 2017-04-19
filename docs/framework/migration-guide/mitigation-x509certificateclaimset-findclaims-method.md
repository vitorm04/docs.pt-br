---
title: "Mitigação: método X509CertificateClaimSet.FindClaims | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c234d6ddeda50dfefff8c49a2e14d623cdd8d861
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Mitigação: método X509CertificateClaimSet.FindClaims
Começando com aplicativos que se destinam ao [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> tentará fazer a correspondência do argumento `claimType` com todas as entradas DNS em seu campo SAN.  
  
## <a name="impact"></a>Impacto  
 Essa alteração afeta somente os aplicativos que se destinam a versões do .NET Framework, começando pelo [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Para aplicativos que se destinam às versões anteriores do .NET Framework, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> tenta fazer a correspondência do argumento `claimType` apenas com a última entrada DNS.  
  
## <a name="mitigation"></a>Redução  
 Se essa alteração for indesejável, os aplicativos que se destinam às versões do .NET Framework, começando com o [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], poderão recusá-la adicionando a seguinte definição de configuração à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:  
  
```xml  
  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
  
```  
  
 Além disso, os aplicativos destinados a versões anteriores do .NET Framework, mas estão sendo executados no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões posteriores, podem aceitar esse comportamento adicionando a seguinte definição de configuração à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:  
  
```xml  
  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
