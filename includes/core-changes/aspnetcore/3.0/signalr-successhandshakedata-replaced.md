---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901722"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>Signalr: HandshakeProtocol. SuccessHandshakeData substituído

O campo [HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) foi removido e substituído por um método auxiliar que gera uma resposta de handshake bem-sucedida devido a um `IHubProtocol`específico.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`HandshakeProtocol.SuccessHandshakeData` foi um campo de `public static ReadOnlyMemory<byte>`.

#### <a name="new-behavior"></a>Novo comportamento

`HandshakeProtocol.SuccessHandshakeData` foi substituído por um método de `GetSuccessfulHandshake(IHubProtocol protocol)` de `static` que retorna uma `ReadOnlyMemory<byte>` com base no protocolo especificado.

#### <a name="reason-for-change"></a>Motivo da alteração

Campos adicionais foram adicionados à _resposta_ de handshake que são não constantes e mudam dependendo do protocolo selecionado.

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma. Esse tipo não é projetado para uso do código do usuário. É `public`, portanto, pode ser compartilhado entre o servidor e o cliente do Signalr. Ele também pode ser usado por clientes do Signalr do cliente escritos em .NET. **Os usuários** do signalr não devem ser afetados por essa alteração.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
