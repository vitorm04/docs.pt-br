---
ms.openlocfilehash: a29f0ca6d235250ac1f41e686178b2d6affcd8a0
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760961"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Chamada para CreateDefaultAuthorizationContext com um argumento nulo foi alterada

|   |   |
|---|---|
|Detalhes|A implementação de <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> retornado por uma chamada a <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> com um argumento authorizationPolicies nulo mudou sua implementação no .NET Framework 4.6.|
|Sugestão|Em casos raros, os aplicativos WCF que usam a autenticação personalizada podem ver diferenças de comportamento. Nesses casos, o comportamento anterior pode ser restaurado de uma destas duas maneiras:<ol><li>Recompile o aplicativo para se destinar a uma versão anterior ao .NET Framework 4.6. Para serviços hospedados pelo IIS, use o elemento &lt;httpRuntime targetFramework=&quot;x.x&quot; /&gt; para destinar a uma versão anterior do .NET Framework.</li><li>Adicione a seguinte linha à seção <code>&lt;appSettings&gt;</code> de seu arquivo app.config: <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|

