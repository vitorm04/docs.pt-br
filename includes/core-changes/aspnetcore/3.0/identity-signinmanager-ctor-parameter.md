---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901851"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identity: o Construtor SignInManager aceita o novo parâmetro

A partir do ASP.NET Core 3,0, um novo parâmetro `IUserConfirmation<TUser>` foi adicionado ao Construtor `SignInManager`. Para obter mais informações, consulte [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da alteração

A motivação para a alteração foi adicionar suporte a novos fluxos de email/confirmação em identidade.

#### <a name="recommended-action"></a>Ação recomendada

Se você construir manualmente uma `SignInManager`, forneça uma implementação de `IUserConfirmation` ou pegue uma da injeção de dependência a ser fornecida.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
