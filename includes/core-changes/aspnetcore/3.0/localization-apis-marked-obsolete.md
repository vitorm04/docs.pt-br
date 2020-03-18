---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901826"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Localização: ResourceManagerWithCultureStringLocalizer e WithCulture marcados como obsoletos

A classe [ResourceManagerWithCultureCultureLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) e o membro da interface [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) são muitas vezes `IStringLocalizer` fontes de confusão para os usuários de localização, especialmente quando criam sua própria implementação. Esses itens dão ao usuário a `IStringLocalizer` impressão de que uma instância é "por idioma, por recurso". Na realidade, as instâncias devem ser apenas "por recurso". A linguagem pesquisada é `CultureInfo.CurrentUICulture` determinada pelo momento da execução. Para eliminar a fonte da confusão, as APIs foram marcadas como obsoletas em ASP.NET O Core 3.0 Preview 3. As APIs serão removidas em uma versão futura.

Para o contexto, consulte [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324). Para discussão, consulte [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Os métodos não `Obsolete`foram marcados como .

#### <a name="new-behavior"></a>Novo comportamento

Os métodos `Obsolete`são marcados .

#### <a name="reason-for-change"></a>Motivo da mudança

As APIs representaram um caso de uso que não é recomendado. Houve confusão sobre o projeto da localização.

#### <a name="recommended-action"></a>Ação recomendada

A recomendação `ResourceManagerStringLocalizer` é usar em seu lugar. Que a cultura seja `CurrentCulture`definida pelo. Se isso não for uma opção, crie e use uma cópia do [ResourceManagerWithCultureCultureLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

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
