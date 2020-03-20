---
title: 'Mitigação: método X509CertificateClaimSet.FindClaims'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: f94a5f685a5aa94332bf2e15e5d5eb0def02d7ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400137"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Mitigação: método X509CertificateClaimSet.FindClaims
Começando com aplicativos direcionados ao .NET Framework 4.6.1, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tentará corresponder o argumento `claimType` com todas as entradas DNS em seu campo SAN.  
  
## <a name="impact"></a>Impacto  
 Essa alteração afeta somente os aplicativos que se destinam a versões do .NET Framework, começando pelo .NET Framework 4.6.1.  
  
 Para aplicativos direcionados a versões anteriores do .NET Framework, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tenta corresponder o argumento `claimType` apenas com a última entrada DNS.  
  
## <a name="mitigation"></a>Atenuação  
 Se essa alteração for indesejável, os aplicativos que têm como destino as versões do .NET Framework a partir do .NET Framework 4.6.1 podem optar por sua configuração adicionando a seguinte configuração à seção [ \<de>em tempo de execução](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 Além disso, os aplicativos que têm como alvo versões anteriores do .NET Framework, mas estão sendo executados o .NET Framework 4.6.1 e versões posteriores podem optar por esse comportamento adicionando a seguinte configuração à configuração em [ \<tempo de execução>](../configure-apps/file-schema/runtime/runtime-element.md) seção do arquivo de configuração do aplicativo:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Confira também

- [Compatibilidade de aplicativos](application-compatibility.md)
