---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345211"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>Signalr: protocolo Hub MessagePack movido para o pacote MessagePack 2. x

O protocolo ASP.NET Core de [Hub MessagePack](/aspnet/core/signalr/messagepackhubprotocol) signalr não usa o [pacote NuGet MessagePack](https://www.nuget.org/packages/MessagePack) para serialização MessagePack. ASP.NET Core 5,0 atualiza o pacote de 1. x para a versão mais recente do pacote 2. x.

Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692).

#### <a name="version-introduced"></a>Versão introduzida

5,0 visualização 1

#### <a name="old-behavior"></a>Comportamento antigo

ASP.NET Core Signalr usou o pacote MessagePack 1. x para serializar e desserializar mensagens MessagePack.

#### <a name="new-behavior"></a>Novo comportamento

ASP.NET Core Signalr usa o pacote MessagePack 2. x para serializar e desserializar mensagens MessagePack.

#### <a name="reason-for-change"></a>Motivo da alteração

As melhorias mais recentes no pacote MessagePack 2. x adicionam uma funcionalidade útil.

#### <a name="recommended-action"></a>Ação recomendada

Essa alteração significativa se aplica quando:

* Definindo ou Configurando valores em <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .
* Usar as APIs do MessagePack diretamente e usar o protocolo Hub MessagePack do ASP.NET Core Signalr no mesmo projeto. A versão mais recente será carregada em vez da versão anterior.

Para obter diretrizes de migração dos autores de pacotes, consulte [migrando do MessagePack v1. x para o MessagePack v2. x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md). Alguns aspectos da serialização e desserialização de mensagens são afetados. Especificamente, há [alterações comportamentais em como os valores de data e hora são serializados](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
