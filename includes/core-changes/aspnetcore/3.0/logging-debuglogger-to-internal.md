---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393998"
---
### <a name="logging-debuglogger-class-made-internal"></a>Registro: Classe DebugLogger feita internamente

Antes de ASP.NET Núcleo `DebugLogger`3.0, o `public`modificador de acesso era . Em ASP.NET Núcleo 3.0, o `internal`modificador de acesso mudou para .

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da mudança

A mudança está sendo feita para:

* Impor consistência com outras implementações `ConsoleLogger`de madeireiros, tais como .
* Reduza a superfície da API.

#### <a name="recommended-action"></a>Ação recomendada

Use <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` o método de extensão para permitir o registro de depuração. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>também está `public` ainda no caso de o serviço precisar ser registrado manualmente.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
