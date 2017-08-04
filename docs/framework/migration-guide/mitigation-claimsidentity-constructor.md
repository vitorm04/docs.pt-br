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
# <a name="mitigation-claimsidentity-constructor"></a>Mitigação: construtor ClaimsIdentity
Começando com o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], há alteração em como o construtor <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> define a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName>. Se o argumento <xref:System.Security.Principal.IIdentity> for um objeto <xref:System.Security.Claims.ClaimsIdentity> e a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> desse objeto <xref:System.Security.Claims.ClaimsIdentity> não for `null`, a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> será anexada usando o método <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName>. No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> é anexada como uma referência existente.  
  
## <a name="impact"></a>Impacto  
 Começando com o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> do novo objeto <xref:System.Security.Claims.ClaimsIdentity> não é igual à propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> do argumento <xref:System.Security.Principal.IIdentity> do construtor. No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e em versões anteriores, ela é igual.  
  
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

