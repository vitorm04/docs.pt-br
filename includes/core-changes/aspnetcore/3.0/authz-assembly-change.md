---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74100640"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorização: sobrecarga de addautoria movida para um assembly diferente

Os métodos Core `AddAuthorization` que costumava residir em `Microsoft.AspNetCore.Authorization` foram renomeados para `AddAuthorizationCore`. Os métodos de `AddAuthorization` antigos ainda existem, mas estão no assembly `Microsoft.AspNetCore.Authorization.Policy` em vez disso. Os aplicativos que usam os dois métodos não devem ter nenhum impacto. Observe que `Microsoft.AspNetCore.Authorization.Policy` agora é fornecido na estrutura compartilhada, em vez de um pacote autônomo, conforme discutido em [estrutura compartilhada: assemblies removidos do Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

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
