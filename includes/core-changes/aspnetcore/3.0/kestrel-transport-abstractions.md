---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393930"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: Abstrações de transporte removidas e divulgadas

Como parte do afastamento das APIs "pubternais", as APIs da camada de `Microsoft.AspNetCore.Connections.Abstractions` transporte Kestrel são expostas como uma interface pública na biblioteca.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

- Abstrações relacionadas ao transporte estavam disponíveis na `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` biblioteca.
- A `ListenOptions.NoDelay` propriedade estava disponível.

#### <a name="new-behavior"></a>Novo comportamento

- A `IConnectionListener` interface foi `Microsoft.AspNetCore.Connections.Abstractions` introduzida na biblioteca para expor `...Transport.Abstractions` a funcionalidade mais usada da biblioteca.
- O `NoDelay` agora está disponível`LibuvTransportOptions` `SocketTransportOptions`em opções de transporte (e ).
- `SchedulingMode`não está mais disponível.

#### <a name="reason-for-change"></a>Motivo da mudança

ASP.NET Core 3.0 se afastou das APIs "pubternais".

#### <a name="recommended-action"></a>Ação recomendada

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

### Affected APIs

Not detectable via API analysis

-->
