---
ms.openlocfilehash: a4bf8cff59ffe01b7465e227c0b1d1e7d93f16e7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394182"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Estrutura compartilhada: assemblies removidos do Microsoft. AspNetCore. app

A partir do ASP.NET Core 3,0, a estrutura compartilhada ASP.NET Core (`Microsoft.AspNetCore.App`) contém apenas assemblies de terceiros que são totalmente desenvolvidos, com suporte e podem ser atendidos pela Microsoft. 

#### <a name="change-description"></a>Alterar descrição

Imagine a alteração como a redefinição de limites para a ASP.NET Core "plataforma". A estrutura compartilhada será [criada de origem por qualquer pessoa por meio do GitHub](https://github.com/dotnet/source-build) e continuará a oferecer os benefícios existentes das estruturas compartilhadas do .NET Core para seus aplicativos. Alguns benefícios incluem tamanho de implantação menor, aplicação de patch centralizada e tempo de inicialização mais rápido.

Como parte da alteração, algumas alterações significativas importantes são introduzidas em `Microsoft.AspNetCore.App`.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Projetos referenciados `Microsoft.AspNetCore.App` por meio de um elemento `<PackageReference>` no arquivo de projeto.

Além disso, `Microsoft.AspNetCore.App` continha os seguintes subcomponentes:

- Json.NET (`Newtonsoft.Json`)
- Entity Framework Core (assemblies prefixados com `Microsoft.EntityFrameworkCore.`)
- Roslyn (`Microsoft.CodeAnalysis`)

#### <a name="new-behavior"></a>Novo comportamento

Uma referência a `Microsoft.AspNetCore.App` não requer mais um elemento `<PackageReference>` no arquivo de projeto. O SDK do .NET Core dá suporte a um novo elemento chamado `<FrameworkReference>`, que substitui o uso de `<PackageReference>`.

Para obter mais informações, consulte [ASPNET/AspNetCore # 3612](https://github.com/aspnet/AspNetCore/issues/3612).

Entity Framework Core são fornecidos como pacotes NuGet. Essa alteração alinha o modelo de envio com todas as outras bibliotecas de acesso a dados no .NET. Ele fornece Entity Framework Core caminho mais simples para continuar inovação enquanto dá suporte a várias plataformas .NET. A mudança de Entity Framework Core da estrutura compartilhada não tem impacto sobre seu status como uma biblioteca de serviços desenvolvidos, com suporte e desenvolvido pela Microsoft. A [política de suporte do .NET Core](https://www.microsoft.com/net/platform/support-policy) continua a cobrir.

Json.NET e Entity Framework Core continuam trabalhando com ASP.NET Core. No entanto, eles não serão incluídos na estrutura compartilhada.

Para obter mais informações, consulte [o futuro do JSON no .NET Core 3,0](https://github.com/dotnet/announcements/issues/90). Consulte também [a lista completa de binários](https://github.com/aspnet/AspNetCore/issues/3755) removidos da estrutura compartilhada.

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração simplifica o consumo de `Microsoft.AspNetCore.App` e reduz a duplicação entre pacotes do NuGet e estruturas compartilhadas.

Para obter mais informações sobre a motivação para essa alteração, consulte [esta postagem no blog](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).

#### <a name="recommended-action"></a>Ação recomendada

Não será necessário que os projetos consumam assemblies em `Microsoft.AspNetCore.App` como pacotes NuGet. Para simplificar o direcionamento e o uso da estrutura ASP.NET Core compartilhada, muitos pacotes NuGet fornecidos desde ASP.NET Core 1,0 não são mais produzidos. As APIs que esses pacotes fornecem ainda estão disponíveis para aplicativos usando um `<FrameworkReference>` a `Microsoft.AspNetCore.App`. Exemplos comuns de API incluem Kestrel, MVC e Razor.

Essa alteração não se aplica a todos os binários referenciados por meio de `Microsoft.AspNetCore.App` em ASP.NET Core 2. x. As exceções notáveis incluem:

- as bibliotecas `Microsoft.Extensions` que continuam a direcionar .NET Standard estarão disponíveis como pacotes NuGet (consulte https://github.com/aspnet/Extensions).
- APIs produzidas pela equipe de ASP.NET Core que não fazem parte do `Microsoft.AspNetCore.App`. Por exemplo, os seguintes componentes estão disponíveis como pacotes NuGet:
  - Entity Framework Core
  - APIs que fornecem integração de terceiros
  - Recursos experimentais
  - APIs com dependências que não puderam [atender aos requisitos para estar na estrutura compartilhada](https://github.com/aspnet/AspNetCore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Extensões para MVC que mantêm suporte para Json.NET. Uma API será fornecida como um pacote NuGet para dar suporte ao uso do Json.NET e MVC.
- O cliente do sinalizador .NET continuará a dar suporte a .NET Standard e enviará como um pacote NuGet. Ele é destinado ao uso em vários tempos de execução do .NET, como Xamarin e UWP.

Para obter mais informações, consulte [parar de produzir pacotes para assemblies de estrutura compartilhada em 3,0](https://github.com/aspnet/AspNetCore/issues/3756). Para obter uma discussão, consulte [ASPNET/AspNetCore # 3757](https://github.com/aspnet/AspNetCore/issues/3757).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
