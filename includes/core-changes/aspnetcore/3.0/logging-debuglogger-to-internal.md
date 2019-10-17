---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393998"
---
### <a name="logging-debuglogger-class-made-internal"></a>Log: classe DebugLogger criada internamente

Antes do ASP.NET Core 3,0, o modificador de acesso de `DebugLogger` era `public`. No ASP.NET Core 3,0, o modificador de acesso foi alterado para `internal`.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da alteração

A alteração está sendo feita para:

* Impor consistência com outras implementações de agente, como `ConsoleLogger`.
* Reduza a superfície da API.

#### <a name="recommended-action"></a>Ação recomendada

Use o método de extensão <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` para habilitar o log de depuração. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> ainda é `public` no caso de o serviço precisar ser registrado manualmente.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
