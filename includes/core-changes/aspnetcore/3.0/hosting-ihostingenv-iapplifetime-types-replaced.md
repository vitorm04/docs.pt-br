---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394334"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hospedagem: IHostingTipos de ambiente e IAppLifetime marcados como obsoletos e substituídos

Novos tipos foram introduzidos `IHostingEnvironment` para `IApplicationLifetime` substituir os tipos e os existentes.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Havia dois `IHostingEnvironment` `IApplicationLifetime` tipos diferentes de `Microsoft.Extensions.Hosting` e `Microsoft.AspNetCore.Hosting`.

#### <a name="new-behavior"></a>Novo comportamento

Os tipos antigos foram marcados como obsoletos e substituídos por novos tipos.

#### <a name="reason-for-change"></a>Motivo da mudança

Quando `Microsoft.Extensions.Hosting` foi introduzido em ASP.NET Núcleo 2.1, alguns tipos gostam `IHostingEnvironment` e `IApplicationLifetime` foram copiados de `Microsoft.AspNetCore.Hosting`. Algumas ASP.NET alterações do Core 3.0 fazem com que os aplicativos incluam os `Microsoft.Extensions.Hosting` espaços de nome e `Microsoft.AspNetCore.Hosting` os seguintes. Qualquer uso desses tipos duplicados causa um erro de compilador de "referência ambígua" quando ambos os namespaces são referenciados.

#### <a name="recommended-action"></a>Ação recomendada

Substituiu todos os usos dos tipos antigos pelos tipos recém-introduzidos conforme abaixo:

**Tipos obsoletos (aviso):**

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

**Novos tipos:**

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

Os `IHostEnvironment` `IsDevelopment` novos `IsProduction` métodos de `Microsoft.Extensions.Hosting` extensão estão no namespace. Esse namespace pode precisar ser adicionado ao seu projeto.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
