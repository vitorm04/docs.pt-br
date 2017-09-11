---
title: "Mitigação: AuthorizationContext Padrão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cfeee63-b148-429a-a7e6-6fe9b0cb7610
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 48363d0f8e515b703e49761a763379566e217844
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-default-authorizationcontext"></a><span data-ttu-id="c03f0-102">Mitigação: AuthorizationContext Padrão</span><span class="sxs-lookup"><span data-stu-id="c03f0-102">Mitigation: Default AuthorizationContext</span></span>
<span data-ttu-id="c03f0-103">A implementação do <xref:System.IdentityModel.Policy.AuthorizationContext> retornado por uma chamada para <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> com um argumento `null``authorizationPolicies` mudou sua implementação no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c03f0-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> with a `null``authorizationPolicies` argument has changed its implementation in the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c03f0-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="c03f0-104">Impact</span></span>  
 <span data-ttu-id="c03f0-105">Em casos raros, os aplicativos WCF que usam a autenticação personalizada podem ver diferenças de comportamento.</span><span class="sxs-lookup"><span data-stu-id="c03f0-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c03f0-106">Redução</span><span class="sxs-lookup"><span data-stu-id="c03f0-106">Mitigation</span></span>  
 <span data-ttu-id="c03f0-107">Você pode restaurar o comportamento anterior usando uma destas duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="c03f0-107">You can restore the previous behavior in either of two ways:</span></span>  
  
-   <span data-ttu-id="c03f0-108">Recompile o aplicativo para se destinar a uma versão anterior ao .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="c03f0-108">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="c03f0-109">Para serviços hospedados pelo IIS, use o elemento `<httpRuntime targetFramework="x.x" />` para direcionar a uma versão anterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c03f0-109">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x" />` element to target an earlier version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="c03f0-110">Adicione a seguinte linha à seção `<appSettings>` de seu arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="c03f0-110">Add the following line to the `<appSettings>` section of your app.config file:</span></span>  
  
    ```xml  
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c03f0-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c03f0-111">See Also</span></span>  
 [<span data-ttu-id="c03f0-112">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="c03f0-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

