---
title: 'Mitigação: método X509CertificateClaimSet.FindClaims'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 0b306960c4f11bb6f54aecaeb13297e7725e16a8
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102639"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="15d6b-102">Mitigação: método X509CertificateClaimSet.FindClaims</span><span class="sxs-lookup"><span data-stu-id="15d6b-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="15d6b-103">Começando com aplicativos que visam o .NET <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Framework 4.6.1, o método tentará combinar o `claimType` argumento com todas as entradas de DNS em seu campo SAN.</span><span class="sxs-lookup"><span data-stu-id="15d6b-103">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="15d6b-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="15d6b-104">Impact</span></span>  
 <span data-ttu-id="15d6b-105">Essa alteração afeta somente os aplicativos que se destinam a versões do .NET Framework, começando pelo .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="15d6b-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="15d6b-106">Para aplicativos direcionados a versões anteriores do .NET Framework, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tenta corresponder o argumento `claimType` apenas com a última entrada DNS.</span><span class="sxs-lookup"><span data-stu-id="15d6b-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="15d6b-107">Atenuação</span><span class="sxs-lookup"><span data-stu-id="15d6b-107">Mitigation</span></span>  
 <span data-ttu-id="15d6b-108">Se essa alteração for indesejável, os aplicativos que têm como destino as versões do .NET Framework a partir do .NET Framework 4.6.1 podem optar por sua configuração adicionando a seguinte configuração à seção [ \<de>em tempo de execução](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="15d6b-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="15d6b-109">Além disso, os aplicativos que têm como alvo versões anteriores do .NET Framework, mas estão sendo executados sob o .NET Framework 4.6.1 e versões posteriores podem optar por esse comportamento adicionando a seguinte configuração à configuração em [ \<tempo de execução>](../configure-apps/file-schema/runtime/runtime-element.md) seção do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="15d6b-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="15d6b-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="15d6b-110">See also</span></span>

- [<span data-ttu-id="15d6b-111">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="15d6b-111">Application compatibility</span></span>](application-compatibility.md)
