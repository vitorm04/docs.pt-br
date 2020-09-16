---
ms.openlocfilehash: 41e80a9dbcfa2a857e0b52674ef0724a542458a0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539437"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a>Localização: classe ResourceManagerWithCultureStringLocalizer e membro da interface WithCulture removidos

A classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) e o método [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) foram removidos no .NET 5,0 Preview 1.

Para contexto, consulte [ASPNET/comunicados # 346](https://github.com/aspnet/Announcements/issues/346) e [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Para discussão sobre essa alteração, consulte [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Versão introduzida

5,0 visualização 1

#### <a name="old-behavior"></a>Comportamento antigo

A `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método são [obsoletos no .NET Core 3,0 Preview 3 e posterior](../../../../docs/core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).

#### <a name="new-behavior"></a>Novo comportamento

A `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método foram removidos no .NET 5,0 Preview 1. Para obter um inventário das alterações feitas, consulte a solicitação pull em [dotnet/Extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files).

#### <a name="reason-for-change"></a>Motivo da alteração

A classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) e o método [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) geralmente eram fontes de confusão para os usuários da localização. A confusão era especialmente alta ao criar uma <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementação personalizada. Essa classe e o método dão aos consumidores a impressão de que uma `IStringLocalizer` instância deve ser "por idioma, por recurso". Na realidade, a instância só deve ser "por recurso". Em tempo de execução, a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> propriedade determina o idioma a ser usado.

#### <a name="recommended-action"></a>Ação recomendada

Pare de usar a `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método.

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
