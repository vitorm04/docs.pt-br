---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522667"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>SPAs: SpaServices e Nodeservices não retornam mais para o agente do console

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> e <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> não exibirão logs do console, a menos que o log esteja configurado.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`Microsoft.AspNetCore.SpaServices` e `Microsoft.AspNetCore.NodeServices` usados para criar automaticamente um agente de log do console quando o registro não estiver configurado.

#### <a name="new-behavior"></a>Novo comportamento

`Microsoft.AspNetCore.SpaServices` e `Microsoft.AspNetCore.NodeServices` não exibirão logs do console, a menos que o log esteja configurado.

#### <a name="reason-for-change"></a>Motivo da alteração

Há a necessidade de se alinhar com o modo como outros pacotes de ASP.NET Core implementam o registro em log.

#### <a name="recommended-action"></a>Ação recomendada

Se o comportamento antigo for necessário, para configurar o log do console, adicione `services.AddLogging(builder => builder.AddConsole())` ao seu método `Setup.ConfigureServices`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!--

#### Affected APIs

Not detectable via API analysis

-->
