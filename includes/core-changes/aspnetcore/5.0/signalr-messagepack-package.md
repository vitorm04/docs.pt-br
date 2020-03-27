---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345211"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>SignalR: MessagePack Hub Protocol mudou para o pacote MessagePack 2.x

O [protocolo](/aspnet/core/signalr/messagepackhubprotocol) do Hub Do SignalR do ASP.NET usa o [pacote MessagePack NuGet](https://www.nuget.org/packages/MessagePack) para serialização messagePack. ASP.NET Core 5.0 atualiza o pacote de 1.x para a versão mais recente do pacote 2.x.

Para discussão sobre este assunto, consulte [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).

#### <a name="version-introduced"></a>Versão introduzida

5.0 Visualização 1

#### <a name="old-behavior"></a>Comportamento antigo

ASP.NET Core SignalR usou o pacote MessagePack 1.x para serializar e desserializar mensagens messagePack.

#### <a name="new-behavior"></a>Novo comportamento

ASP.NET Core SignalR usa o pacote MessagePack 2.x para serializar e desserializar mensagens messagePack.

#### <a name="reason-for-change"></a>Motivo da mudança

As melhorias mais recentes no pacote MessagePack 2.x adicionam funcionalidade útil.

#### <a name="recommended-action"></a>Ação recomendada

Esta mudança de quebra se aplica quando:

* Configuração ou configuração de valores em <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.
* Usando as APIs messagePack diretamente e usando o protocolo do Hub do SignalR Do ASP.NET no mesmo projeto. A versão mais recente será carregada em vez da versão anterior.

Para obter orientação de migração dos autores do pacote, consulte [Migrando de MessagePack v1.x para MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md). Alguns aspectos da serialização e desserialização das mensagens são afetados. Especificamente, há [mudanças comportamentais na forma como os valores do DateTime são serializados](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
