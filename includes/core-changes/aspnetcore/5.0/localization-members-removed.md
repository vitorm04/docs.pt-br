---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728282"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a>Localização: classe ResourceManagerWithCultureStringLocalizer e membro da interface WithCulture removidos

A classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) e o método [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) foram removidos no .NET 5,0 Preview 1.

Para contexto, consulte [ASPNET/comunicados # 346](https://github.com/aspnet/Announcements/issues/346) e [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Para discussão sobre essa alteração, consulte [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Versão introduzida

5,0 visualização 1

#### <a name="old-behavior"></a>Comportamento antigo

A `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método são [obsoletos no .NET Core 3,0 Preview 3 e posterior](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).

#### <a name="new-behavior"></a>Novo comportamento

A `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método foram removidos no .NET 5,0 Preview 1. Para obter um inventário das alterações feitas, consulte a solicitação pull em [dotnet/Extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files).

#### <a name="reason-for-change"></a>Motivo da alteração

A classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) e o método [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) geralmente eram fontes de confusão para os usuários da localização. A confusão era especialmente alta ao criar uma implementação <xref:Microsoft.Extensions.Localization.IStringLocalizer> personalizada. Essa classe e o método dão aos consumidores a impressão `IStringLocalizer` de que uma instância deve ser "por idioma, por recurso". Na realidade, a instância só deve ser "por recurso". Em tempo de execução, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> a propriedade determina o idioma a ser usado.

#### <a name="recommended-action"></a>Ação recomendada

Pare de usar `ResourceManagerWithCultureStringLocalizer` a classe e `ResourceManagerStringLocalizer.WithCulture` o método.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
