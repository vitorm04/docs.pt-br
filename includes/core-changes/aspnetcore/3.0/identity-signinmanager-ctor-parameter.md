---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275164"
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

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
