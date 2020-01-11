---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901666"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>Signalr: métodos HubConnection ResetSendPing e ResetTimeout removidos

Os métodos `ResetSendPing` e `ResetTimeout` foram removidos da API do Signalr `HubConnection`. Esses métodos eram originalmente destinados apenas ao uso interno, mas foram disponibilizados para o público em ASP.NET Core 2,2. Esses métodos não estarão disponíveis a partir da versão ASP.NET Core 3,0 Preview 4. Para obter uma discussão, consulte [dotnet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

APIs estavam disponíveis.

#### <a name="new-behavior"></a>Novo comportamento

As APIs são removidas.

#### <a name="reason-for-change"></a>Motivo da alteração

Esses métodos eram originalmente destinados apenas ao uso interno, mas foram disponibilizados para o público em ASP.NET Core 2,2.

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
