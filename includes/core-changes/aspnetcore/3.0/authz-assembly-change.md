---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394265"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorização: sobrecarga de addautoria movida para um assembly diferente

Os métodos Core `AddAuthorization` que costumava residir em `Microsoft.AspNetCore.Authorization` foram renomeados para `AddAuthorizationCore`. Os métodos antigos de `AddAuthorization` ainda existem, mas estão no pacote `Microsoft.AspNetCore.Authorization.Policy`, em vez disso. Os aplicativos que usam os dois métodos não devem ter nenhum impacto. Os aplicativos que não estavam usando o pacote de política devem mudar para usando `AddAuthorizationCore`.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

os métodos `AddAuthorization` existiam no `Microsoft.AspNetCore.Authorization`.

#### <a name="new-behavior"></a>Novo comportamento

os métodos `AddAuthorization` existem no `Microsoft.AspNetCore.Authorization.Policy`. `AddAuthorizationCore` é o novo nome para os métodos antigos.

#### <a name="reason-for-change"></a>Motivo da alteração

`AddAuthorization` é um nome de método melhor para adicionar todos os serviços comuns necessários para autorização.

#### <a name="recommended-action"></a>Ação recomendada

Adicione uma referência a `Microsoft.AspNetCore.Authorization.Policy` ou use `AddAuthorizationCore` em vez disso.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
