---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393930"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: abstrações de transporte removidas e tornadas públicas

Como parte da afastamento das APIs "pubternal", as APIs da camada de transporte do Kestrel são expostas como uma interface pública na biblioteca `Microsoft.AspNetCore.Connections.Abstractions`.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

- Abstrações relacionadas ao transporte estavam disponíveis na biblioteca `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions`.
- A propriedade `ListenOptions.NoDelay` estava disponível.

#### <a name="new-behavior"></a>Novo comportamento

- A interface `IConnectionListener` foi introduzida na biblioteca `Microsoft.AspNetCore.Connections.Abstractions` para expor a funcionalidade mais usada da biblioteca `...Transport.Abstractions`.
- O `NoDelay` agora está disponível nas opções de transporte (`LibuvTransportOptions` e `SocketTransportOptions`).
- `SchedulingMode` não está mais disponível.

#### <a name="reason-for-change"></a>Motivo da alteração

ASP.NET Core 3,0 foi afastado das APIs "pubternal".

#### <a name="recommended-action"></a>Ação recomendada

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

### Affected APIs

Not detectable via API analysis

-->
