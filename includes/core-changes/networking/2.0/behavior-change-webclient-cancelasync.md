---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859631"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a>WebClient. CancelAsync nem sempre cancela imediatamente

A partir do .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> a chamada não cancelará a solicitação imediatamente se a resposta tiver começado a ser buscada.

#### <a name="change-description"></a>Descrição da alteração

Anteriormente, chamar <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> cancelou a solicitação imediatamente. A partir do .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> chamar cancelará a solicitação imediatamente somente se a resposta não tiver começado a busca. Se a resposta tiver começado a ser buscada, a solicitação será cancelada somente depois que uma resposta completa for lida.

Essa alteração foi implementada porque <xref:System.Net.WebClient> a API foi preterida em <xref:System.Net.Http.HttpClient>favor de.

#### <a name="version-introduced"></a>Versão introduzida

2,0

#### <a name="recommended-action"></a>Ação recomendada

Use a <xref:System.Net.Http.HttpClient?displayProperty=fullName> classe em vez <xref:System.Net.WebClient?displayProperty=fullName>de, que é preterida.

#### <a name="category"></a>Categoria

Rede

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
