---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901826"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Localização: ResourceManagerWithCultureStringLocalizer e WithCulture marcados como obsoletos

A classe [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) e o membro da interface [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) geralmente são fontes de confusão para os usuários da localização, especialmente ao criar sua própria implementação de `IStringLocalizer`. Esses itens dão ao usuário a impressão de que uma instância de `IStringLocalizer` é "por idioma, por recurso". Na realidade, as instâncias só devem ser "por recurso". O idioma pesquisado é determinado pelo `CultureInfo.CurrentUICulture` no momento da execução. Para eliminar a origem da confusão, as APIs foram marcadas como obsoletas no ASP.NET Core 3,0 Preview 3. As APIs serão removidas em uma versão futura.

Para o contexto, consulte [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Para obter uma discussão, consulte [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Os métodos não estavam marcados como `Obsolete`.

#### <a name="new-behavior"></a>Novo comportamento

Os métodos são marcados `Obsolete`.

#### <a name="reason-for-change"></a>Motivo da alteração

As APIs representaram um caso de uso que não é recomendado. Houve uma confusão sobre o design da localização.

#### <a name="recommended-action"></a>Ação recomendada

A recomendação é usar `ResourceManagerStringLocalizer` em vez disso. Permita que a cultura seja definida pelo `CurrentCulture`. Se essa não for uma opção, crie e use uma cópia de [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
