---
ms.openlocfilehash: fa0f54404d1e14afa6ce48a425c984a48498a1ee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394031"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>Signalr: HandshakeProtocol. SuccessHandshakeData substituído

O campo [HandshakeProtocol. SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) foi removido e substituído por um método auxiliar que gera uma resposta de handshake com êxito, dado um `IHubProtocol` específico. 

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`HandshakeProtocol.SuccessHandshakeData` era um campo `public static ReadOnlyMemory<byte>`.

#### <a name="new-behavior"></a>Novo comportamento

`HandshakeProtocol.SuccessHandshakeData` foi substituído por um método `static` `GetSuccessfulHandshake(IHubProtocol protocol)` que retorna um `ReadOnlyMemory<byte>` com base no protocolo especificado. 

#### <a name="reason-for-change"></a>Motivo da alteração

Campos adicionais foram adicionados à _resposta_ de handshake que são não constantes e mudam dependendo do protocolo selecionado.

#### <a name="recommended-action"></a>Ação recomendada

nenhuma. Esse tipo não é projetado para uso do código do usuário. É `public`, para que possa ser compartilhado entre o servidor e o cliente do Signalr. Ele também pode ser usado por clientes do Signalr do cliente escritos em .NET. **Os usuários** do signalr não devem ser afetados por essa alteração.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
