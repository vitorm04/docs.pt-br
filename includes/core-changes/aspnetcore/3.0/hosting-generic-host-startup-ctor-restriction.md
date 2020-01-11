---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901777"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hospedagem: host genérico restringe injeção de construtor de inicialização

Os únicos tipos aos quais o host genérico dá suporte para injeção de construtor de classe `Startup` são `IHostEnvironment`, `IWebHostEnvironment`e `IConfiguration`. Os aplicativos que usam `WebHost` não são afetados.

#### <a name="change-description"></a>Descrição das alterações

Antes do ASP.NET Core 3,0, a injeção de Construtor poderia ser usada para tipos arbitrários no construtor da classe `Startup`. No ASP.NET Core 3,0, a pilha da Web foi replataforma na biblioteca de hosts genérica. Você pode ver a alteração no arquivo *Program.cs* dos modelos:

**ASP.NET Core 2. x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host` usa um contêiner de injeção de dependência (DI) para compilar o aplicativo. `WebHost` usa dois contêineres: um para o host e outro para o aplicativo. Como resultado, o Construtor `Startup` não oferece mais suporte à injeção de serviço personalizado. Somente `IHostEnvironment`, `IWebHostEnvironment`e `IConfiguration` podem ser injetados. Essa alteração impede problemas de DI como a criação duplicada de um serviço singleton.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração é uma consequência da replataforma da pilha da Web na biblioteca de hosts genérica.

#### <a name="recommended-action"></a>Ação recomendada

Injetar serviços na assinatura do método de `Startup.Configure`. Por exemplo:

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

{1&gt;Nenhum&lt;1}

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
