---
title: "Mitigação: construtor ClaimsIdentity | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84016664708b9b7fc61a9535e5f7910417caa6f1
ms.contentlocale: pt-br
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-claimsidentity-constructor"></a>Mitigação: construtor ClaimsIdentity
A partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], há uma mudança na forma como o construtor <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> define a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName>. Se o argumento <xref:System.Security.Principal.IIdentity> for um objeto <xref:System.Security.Claims.ClaimsIdentity> e a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> desse objeto <xref:System.Security.Claims.ClaimsIdentity> não for `null`, a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> será anexada usando o método <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName>. No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> está anexada como uma referência existente.  
  
## <a name="impact"></a>Impacto  
 A partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> do novo objeto <xref:System.Security.Claims.ClaimsIdentity> não é igual à propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> do argumento <xref:System.Security.Principal.IIdentity> do construtor. No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e em versões anteriores, ela é igual.  
  
## <a name="mitigation"></a>Redução  
 Se esse comportamento for indesejável, restaure o comportamento anterior definindo a opção `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` no arquivo de configuração do aplicativo como `true`. Isso exige a adição do seguinte à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo web.config:  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

