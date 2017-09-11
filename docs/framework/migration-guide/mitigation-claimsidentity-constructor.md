---
title: "Mitigação: construtor ClaimsIdentity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 946903f1-0fbf-4f67-805b-1eb48352024d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a50cbd69aa1f2c72adc9fc4d10a070f5faa0cf54
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-claimsidentity-constructor"></a><span data-ttu-id="afad7-102">Mitigação: construtor ClaimsIdentity</span><span class="sxs-lookup"><span data-stu-id="afad7-102">Mitigation: ClaimsIdentity Constructor</span></span>
<span data-ttu-id="afad7-103">Começando com o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], há alteração em como o construtor <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> define a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="afad7-103">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], there is change in how the <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> constructor sets the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property.</span></span> <span data-ttu-id="afad7-104">Se o argumento <xref:System.Security.Principal.IIdentity> for um objeto <xref:System.Security.Claims.ClaimsIdentity> e a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> desse objeto <xref:System.Security.Claims.ClaimsIdentity> não for `null`, a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> será anexada usando o método <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="afad7-104">If the <xref:System.Security.Principal.IIdentity> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="afad7-105">No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> é anexada como uma referência existente.</span><span class="sxs-lookup"><span data-stu-id="afad7-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property is attached as a  existing reference.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="afad7-106">Impacto</span><span class="sxs-lookup"><span data-stu-id="afad7-106">Impact</span></span>  
 <span data-ttu-id="afad7-107">Começando com o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> do novo objeto <xref:System.Security.Claims.ClaimsIdentity> não é igual à propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> do argumento <xref:System.Security.Principal.IIdentity> do construtor.</span><span class="sxs-lookup"><span data-stu-id="afad7-107">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity> argument.</span></span> <span data-ttu-id="afad7-108">No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e em versões anteriores, ela é igual.</span><span class="sxs-lookup"><span data-stu-id="afad7-108">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, it is equal.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="afad7-109">Redução</span><span class="sxs-lookup"><span data-stu-id="afad7-109">Mitigation</span></span>  
 <span data-ttu-id="afad7-110">Se esse comportamento for indesejável, restaure o comportamento anterior definindo a opção `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` no arquivo de configuração do aplicativo como `true`.</span><span class="sxs-lookup"><span data-stu-id="afad7-110">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="afad7-111">Isso exige a adição do seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo web.config:</span><span class="sxs-lookup"><span data-stu-id="afad7-111">This requires that you add the following to  the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your web.config file:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="afad7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afad7-112">See Also</span></span>  
 [<span data-ttu-id="afad7-113">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="afad7-113">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

