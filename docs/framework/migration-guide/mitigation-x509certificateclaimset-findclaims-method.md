---
title: 'Mitigação: método X509CertificateClaimSet.FindClaims'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: e75b1cae599b153012b8525a0e1e36ed116e695f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457758"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="596fd-102">Mitigação: método X509CertificateClaimSet.FindClaims</span><span class="sxs-lookup"><span data-stu-id="596fd-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="596fd-103">Começando com aplicativos direcionados ao .NET Framework 4.6.1, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tentará corresponder o argumento `claimType` com todas as entradas DNS em seu campo SAN.</span><span class="sxs-lookup"><span data-stu-id="596fd-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="596fd-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="596fd-104">Impact</span></span>  
 <span data-ttu-id="596fd-105">Essa alteração afeta somente os aplicativos que se destinam a versões do .NET Framework, começando pelo .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="596fd-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="596fd-106">Para aplicativos direcionados a versões anteriores do .NET Framework, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tenta corresponder o argumento `claimType` apenas com a última entrada DNS.</span><span class="sxs-lookup"><span data-stu-id="596fd-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="596fd-107">Redução</span><span class="sxs-lookup"><span data-stu-id="596fd-107">Mitigation</span></span>  
 <span data-ttu-id="596fd-108">Se essa alteração for indesejável, aplicativos que se destinarem ao .NET Framework 4.6.1 ou a uma versão posterior poderão recusá-la adicionando a seguinte definição de configuração à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="596fd-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="596fd-109">Além disso, os aplicativos direcionados a versões anteriores do .NET Framework, mas executados no .NET Framework 4.6.1 e nas versões posteriores, podem escolher adotar esse comportamento adicionando a definição de configuração a seguir à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="596fd-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="596fd-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="596fd-110">See also</span></span>

- [<span data-ttu-id="596fd-111">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="596fd-111">Application compatibility</span></span>](application-compatibility.md)
