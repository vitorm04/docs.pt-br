---
title: 'Mitigação: Método X509CertificateClaimSet.FindClaims'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffc03e6c88a2aabb967587d8b1ee7d0b784b4e7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778939"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="5c5bb-102">Mitigação: Método X509CertificateClaimSet.FindClaims</span><span class="sxs-lookup"><span data-stu-id="5c5bb-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="5c5bb-103">Começando com aplicativos direcionados ao .NET Framework 4.6.1, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tentará corresponder o argumento `claimType` com todas as entradas DNS em seu campo SAN.</span><span class="sxs-lookup"><span data-stu-id="5c5bb-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5c5bb-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="5c5bb-104">Impact</span></span>  
 <span data-ttu-id="5c5bb-105">Essa alteração afeta somente os aplicativos que se destinam a versões do .NET Framework, começando pelo .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="5c5bb-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="5c5bb-106">Para aplicativos direcionados a versões anteriores do .NET Framework, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tenta corresponder o argumento `claimType` apenas com a última entrada DNS.</span><span class="sxs-lookup"><span data-stu-id="5c5bb-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5c5bb-107">Redução</span><span class="sxs-lookup"><span data-stu-id="5c5bb-107">Mitigation</span></span>  
 <span data-ttu-id="5c5bb-108">Se essa alteração for indesejável, aplicativos que se destinarem ao .NET Framework 4.6.1 ou a uma versão posterior poderão recusá-la adicionando a seguinte definição de configuração à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5c5bb-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="5c5bb-109">Além disso, os aplicativos direcionados a versões anteriores do .NET Framework, mas executados no .NET Framework 4.6.1 e nas versões posteriores, podem escolher adotar esse comportamento adicionando a definição de configuração a seguir à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5c5bb-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c5bb-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c5bb-110">See also</span></span>

- [<span data-ttu-id="5c5bb-111">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="5c5bb-111">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
