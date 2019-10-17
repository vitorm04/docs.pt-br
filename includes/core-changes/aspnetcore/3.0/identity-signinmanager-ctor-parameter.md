---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393892"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identity: o Construtor SignInManager aceita o novo parâmetro

A partir do ASP.NET Core 3,0, um novo parâmetro `IUserConfirmation<TUser>` foi adicionado ao Construtor `SignInManager`. Para obter mais informações, consulte [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da alteração

A motivação para a alteração foi adicionar suporte a novos fluxos de email/confirmação em identidade.

#### <a name="recommended-action"></a>Ação recomendada

Se você construir manualmente um `SignInManager`, forneça uma implementação de `IUserConfirmation` ou pegue um da injeção de dependência a ser fornecida.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
