---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901722"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR: HandshakeProtocol.SuccessHandshakeData substituído

O campo [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) foi removido e substituído por um método auxiliar `IHubProtocol`que gera uma resposta de aperto de mão bem sucedida dada uma resposta específica .

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`HandshakeProtocol.SuccessHandshakeData`era `public static ReadOnlyMemory<byte>` um campo.

#### <a name="new-behavior"></a>Novo comportamento

`HandshakeProtocol.SuccessHandshakeData`foi substituído por `static` `GetSuccessfulHandshake(IHubProtocol protocol)` um método `ReadOnlyMemory<byte>` que retorna um com base no protocolo especificado.

#### <a name="reason-for-change"></a>Motivo da mudança

Campos adicionais foram adicionados à _resposta_ de aperto de mão que não são constantes e mudam dependendo do protocolo selecionado.

#### <a name="recommended-action"></a>Ação recomendada

Nenhum. Este tipo não foi projetado para ser usado a partir do código do usuário. É `public`, para que possa ser compartilhado entre o servidor SignalR e o cliente. Também pode ser usado por clientes SignalR gravados em .NET. **Os usuários** do SignalR não devem ser afetados por essa mudança.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
