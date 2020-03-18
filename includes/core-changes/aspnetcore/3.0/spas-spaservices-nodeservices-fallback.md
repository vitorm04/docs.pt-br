---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522667"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>SPAs: SpaServices e NodeServices não voltam mais para o logger do console

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>e <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> não exibirá registros do console a menos que o registro esteja configurado.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`Microsoft.AspNetCore.SpaServices`e `Microsoft.AspNetCore.NodeServices` usado para criar automaticamente um logger de console quando o registro não é configurado.

#### <a name="new-behavior"></a>Novo comportamento

`Microsoft.AspNetCore.SpaServices`e `Microsoft.AspNetCore.NodeServices` não exibirá registros do console a menos que o registro esteja configurado.

#### <a name="reason-for-change"></a>Motivo da mudança

Há uma necessidade de se alinhar com a forma como outros pacotes ASP.NET Core implementam o registro.

#### <a name="recommended-action"></a>Ação recomendada

Se o comportamento antigo for necessário, para `services.AddLogging(builder => builder.AddConsole())` configurar `Setup.ConfigureServices` o registro do console, adicione ao seu método.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!--

#### Affected APIs

Not detectable via API analysis

-->
