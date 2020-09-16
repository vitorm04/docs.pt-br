---
ms.openlocfilehash: 62a5f56bb7fffc453623a2c3202f288a19110158
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539436"
---
### <a name="localization-pubternal-apis-removed"></a>Localização: APIs "Pubternal" removidas

Para manter melhor a superfície da API pública do ASP.NET Core, algumas :::no-loc text="\"pubternal\""::: APIs de localização foram removidas. Uma :::no-loc text="\"pubternal\""::: API tem um `public` modificador de acesso e é definida em um namespace que implica uma intenção [interna](../../../../docs/csharp/language-reference/keywords/internal.md) .

Para obter uma discussão, consulte [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).

#### <a name="version-introduced"></a>Versão introduzida

5,0 Preview 6

#### <a name="old-behavior"></a>Comportamento antigo

As seguintes APIs foram `public` :

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` sobrecargas de Construtor aceitam qualquer um dos seguintes tipos de parâmetro:
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a>Novo comportamento

A lista a seguir descreve as alterações:

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`já se tornou e agora é `internal` .
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`já se tornou e agora é `internal` .
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` as sobrecargas de construtor que aceitam qualquer um dos seguintes tipos de parâmetro agora são `internal` :
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a>Motivo da alteração

Explicado mais detalhadamente em [ASPNET/comunicados # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), os :::no-loc text="\"pubternal\""::: tipos foram removidos da `public` superfície da API. Essas alterações se adaptam a mais classes para essa decisão de design. As classes em questão eram pretendidas como pontos de extensão para os testes internos da equipe.

#### <a name="recommended-action"></a>Ação recomendada

Embora seja improvável, alguns aplicativos podem depender intencionalmente ou acidentalmente, dependendo dos :::no-loc text="\"pubternal\""::: tipos. Consulte as [novas](#new-behavior) seções de comportamento para determinar como migrar para fora dos tipos.

Se você identificou um cenário que a API pública permitiu antes dessa alteração, mas não agora, execute um problema em [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
