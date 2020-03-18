---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901851"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identidade: O construtor SignInManager aceita novo parâmetro

Começando com ASP.NET Núcleo 3.0, um `IUserConfirmation<TUser>` novo `SignInManager` parâmetro foi adicionado ao construtor. Para obter mais informações, consulte [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da mudança

A motivação para a mudança foi adicionar suporte para novos fluxos de e-mail/confirmação em Identidade.

#### <a name="recommended-action"></a>Ação recomendada

Se construir manualmente `SignInManager`um , `IUserConfirmation` forneça uma implementação ou pegue uma da injeção de dependência para fornecer.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
