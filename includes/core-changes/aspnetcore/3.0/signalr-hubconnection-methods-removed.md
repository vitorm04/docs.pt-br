---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901666"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>SignalR: HubConnection ResetAndo e resetMétodos de tempo de tempo removidos

Os `ResetSendPing` `ResetTimeout` métodos e métodos `HubConnection` foram removidos da API SignalR. Esses métodos foram originalmente destinados apenas para uso interno, mas foram tornados públicos em ASP.NET Núcleo 2.2. Esses métodos não estarão disponíveis a partir da versão ASP.NET Core 3.0 Preview 4. Para discussão, consulte [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

APIs estavam disponíveis.

#### <a name="new-behavior"></a>Novo comportamento

ApIs são removidos.

#### <a name="reason-for-change"></a>Motivo da mudança

Esses métodos foram originalmente destinados apenas para uso interno, mas foram tornados públicos em ASP.NET Núcleo 2.2.

#### <a name="recommended-action"></a>Ação recomendada

Não use esses métodos.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
