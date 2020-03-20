---
ms.openlocfilehash: 9ec5fa379556dedeaa7a35e34f004340ab47a39c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804542"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Chamada para CreateDefaultAuthorizationContext com um argumento nulo foi alterada

|   |   |
|---|---|
|Detalhes|A implementação de <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> retornado por uma chamada a <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> com um argumento authorizationPolicies nulo mudou sua implementação no .NET Framework 4.6.|
|Sugestão|Em casos raros, os aplicativos WCF que usam a autenticação personalizada podem ver diferenças de comportamento. Nesses casos, o comportamento anterior pode ser restaurado de uma destas duas maneiras:<ol><li>Recompile o aplicativo para se destinar a uma versão anterior ao .NET Framework 4.6. Para serviços hospedados pelo IIS, use o elemento &lt;httpRuntime targetFramework=&quot;x.x&quot; /&gt; para destinar a uma versão anterior do .NET Framework.</li><li>Adicione a seguinte linha à seção <code>&lt;appSettings&gt;</code> de seu arquivo app.config: <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Escopo|Secundária|
|Versão|4.6|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|
