---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901777"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hospedagem: Host genérico restringe injeção de construtor de inicialização

Os únicos tipos que o `Startup` host genérico `IHostEnvironment`suporta `IWebHostEnvironment`para `IConfiguration`injeção de construtor de classe são , e . Os `WebHost` aplicativos que usam não são afetados.

#### <a name="change-description"></a>Descrição da alteração

Antes de ASP.NET Núcleo 3.0, a injeção de construtor `Startup` podia ser usada para tipos arbitrários no construtor da classe. Em ASP.NET Core 3.0, a pilha da Web foi replataformada na biblioteca de host genérica. Você pode ver a alteração no arquivo *Program.cs* dos modelos:

**núcleo ASP.NET 2.x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Núcleo 3.0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host`usa um recipiente di de injeção de dependência para construir o aplicativo. `WebHost`usa dois contêineres: um para o host e outro para o aplicativo. Como resultado, `Startup` o construtor não suporta mais injeção de serviço personalizado. Somente `IHostEnvironment` `IWebHostEnvironment`, `IConfiguration` e pode ser injetado. Essa alteração evita problemas de DI, como a criação duplicada de um serviço de singleton.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da mudança

Essa mudança é uma consequência da replataforma da pilha web na biblioteca de host genérica.

#### <a name="recommended-action"></a>Ação recomendada

Injete `Startup.Configure` serviços na assinatura do método. Por exemplo: 

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
