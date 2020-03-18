---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74100640"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorização: Adicionar Sobrecarga de autorização movida para diferentes conjuntos

Os `AddAuthorization` métodos centrais que `Microsoft.AspNetCore.Authorization` costumavam `AddAuthorizationCore`residir foram renomeados para . Os `AddAuthorization` métodos antigos ainda existem, mas estão na `Microsoft.AspNetCore.Authorization.Policy` montagem em vez disso. Os aplicativos que usam ambos os métodos não devem ver nenhum impacto. Observe `Microsoft.AspNetCore.Authorization.Policy` que agora é enviado no framework compartilhado em vez de um pacote autônomo como discutido no [Framework Compartilhado: Conjuntos removidos do Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo
`AddAuthorization`métodos existiam `Microsoft.AspNetCore.Authorization`em .

#### <a name="new-behavior"></a>Novo comportamento

`AddAuthorization`métodos existem em `Microsoft.AspNetCore.Authorization.Policy`. `AddAuthorizationCore`é o novo nome para os métodos antigos.

#### <a name="reason-for-change"></a>Motivo da mudança

`AddAuthorization`é um nome de método melhor para adicionar todos os serviços comuns necessários para autorização.

#### <a name="recommended-action"></a>Ação recomendada

Adicione uma referência `Microsoft.AspNetCore.Authorization.Policy` ou `AddAuthorizationCore` use em vez disso.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
