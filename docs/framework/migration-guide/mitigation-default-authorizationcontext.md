---
title: "Mitigação: AuthorizationContext Padrão | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d2cffc531efc0f0be841956d3a09e1ab253d8fbd
ms.contentlocale: pt-br
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-default-authorizationcontext"></a>Mitigação: AuthorizationContext Padrão
A implementação do <xref:System.IdentityModel.Policy.AuthorizationContext> retornado por uma chamada ao <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> com um argumento `null``authorizationPolicies` alterou sua implementação no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].  
  
## <a name="impact"></a>Impacto  
 Em casos raros, os aplicativos WCF que usam a autenticação personalizada podem ver diferenças de comportamento.  
  
## <a name="mitigation"></a>Redução  
 Você pode restaurar o comportamento anterior usando uma destas duas maneiras:  
  
-   Recompile o aplicativo para se destinar a uma versão anterior ao .NET Framework 4.6. Para serviços hospedados pelo IIS, use o elemento `<httpRuntime targetFramework="x.x" />` para direcionar a uma versão anterior do .NET Framework.  
  
-   Adicione a seguinte linha à seção `<appSettings>` de seu arquivo app.config:  
  
    ```xml  
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
