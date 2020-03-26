---
ms.openlocfilehash: 64e854b06895ca54a9ab9870b85868788a731c00
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549607"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Estrutura compartilhada: Assembléias removidas do Microsoft.AspNetCore.App

A partir de ASP.NET Core 3.0,`Microsoft.AspNetCore.App`o ASP.NET Core () contém apenas montagens de primeira parte que são totalmente desenvolvidas, suportadas e reparadas pela Microsoft.

#### <a name="change-description"></a>Descrição da alteração

Pense na mudança como a redefinição de limites para a "plataforma" ASP.NET Core. A estrutura compartilhada será [construída por qualquer pessoa via GitHub](https://github.com/dotnet/source-build) e continuará a oferecer os benefícios existentes das estruturas compartilhadas do .NET Core aos seus aplicativos. Alguns benefícios incluem menor tamanho de implantação, patches centralizados e tempo de inicialização mais rápido.

Como parte da mudança, algumas mudanças `Microsoft.AspNetCore.App`notáveis de quebra são introduzidas em .

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Projetos referenciados `Microsoft.AspNetCore.App` `<PackageReference>` através de um elemento no arquivo do projeto.

Além disso, `Microsoft.AspNetCore.App` continha os seguintes subcomponentes:

- `Newtonsoft.Json`Json.NET
- Núcleo de Quadro de Entidades (conjuntos prefixados com `Microsoft.EntityFrameworkCore.`)
- Roslyn`Microsoft.CodeAnalysis`( )

#### <a name="new-behavior"></a>Novo comportamento

Uma referência `Microsoft.AspNetCore.App` a não `<PackageReference>` mais requer um elemento no arquivo do projeto. O .NET Core SDK suporta `<FrameworkReference>`um novo elemento chamado `<PackageReference>`, que substitui o uso de .

Para obter mais informações, consulte [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).

Entity Framework Core é enviado como pacotes NuGet. Essa alteração alinha o modelo de envio com todas as outras bibliotecas de acesso a dados no .NET. Ele fornece ao Entity Framework Core o caminho mais simples para continuar inovando enquanto suporta as várias plataformas .NET. A mudança do Entity Framework Core para fora da estrutura compartilhada não tem impacto em seu status como uma biblioteca desenvolvida pela Microsoft, suportada e útil. A [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) continua a cobri-la.

Json.NET e Entity Framework Core continuam a trabalhar com ASP.NET Core. Eles não serão, no entanto, incluídos no quadro compartilhado.

Para obter mais informações, consulte [O futuro do JSON no .NET Core 3.0](https://github.com/dotnet/announcements/issues/90). Veja também [a lista completa de binários removidos](https://github.com/dotnet/aspnetcore/issues/3755) da estrutura compartilhada.

#### <a name="reason-for-change"></a>Motivo da mudança

Essa alteração simplifica o `Microsoft.AspNetCore.App` consumo e reduz a duplicação entre pacotes NuGet e frameworks compartilhados.

Para obter mais informações sobre a motivação dessa mudança, consulte [este post no blog](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="recommended-action"></a>Ação recomendada

Não será necessário que os projetos consumam montagens como `Microsoft.AspNetCore.App` pacotes NuGet. Para simplificar a segmentação e o uso da estrutura compartilhada ASP.NET Core, muitos pacotes NuGet enviados desde ASP.NET Core 1.0 não são mais produzidos. As APIs que esses pacotes fornecem ainda `<FrameworkReference>` `Microsoft.AspNetCore.App`estão disponíveis para os aplicativos usando um a. Exemplos comuns de API incluem Kestrel, MVC e Razor.

Esta alteração não se aplica a todos `Microsoft.AspNetCore.App` os binários referenciados através de ASP.NET Core 2.x. Exceções notáveis incluem:

- `Microsoft.Extensions`bibliotecas que continuam a segmentar .NET Standard estarão https://github.com/dotnet/extensions)disponíveis como pacotes NuGet (veja .
- APIs produzidas pela equipe do ASP.NET `Microsoft.AspNetCore.App`Core que não fazem parte de . Por exemplo, os seguintes componentes estão disponíveis como pacotes NuGet:
  - Entity Framework Core
  - APIs que fornecem integração de terceiros
  - Recursos experimentais
  - APIs com dependências que não poderiam [cumprir os requisitos para estar no quadro compartilhado](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Extensões ao MVC que mantêm suporte para Json.NET. Uma API será fornecida como um pacote NuGet para suportar o uso de Json.NET e MVC.
- O cliente SignalR .NET continuará a suportar o .NET Standard e a enviar como um pacote NuGet. Destina-se a ser usado em muitos runtimes .NET, como Xamarin e UWP.

Para obter mais informações, consulte [Pare de produzir pacotes para montagens de quadros compartilhados em 3.0](https://github.com/dotnet/aspnetcore/issues/3756). Para discussão, consulte [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).

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
