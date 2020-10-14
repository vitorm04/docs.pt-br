---
ms.openlocfilehash: 16994e9cd97b31a30c8c5ce49d2042ff79b3f60b
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050502"
---
### <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a>NegotiateStream e SslStream permitem operações de início sucessivas

Casos de erro em fluxos de segurança são tratados de forma diferente e chamadas sucessivas para `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` podem não falhar mais.

#### <a name="version-introduced"></a>Versão introduzida

RC1 5,0

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, chamando `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` sucessivamente sem primeiro chamar `EndAuthenticateAsServer` ou `EndAuthenticateAsClient` resultar em um <xref:System.NotSupportedException> . A partir do .NET 5,0, as chamadas sucessivas `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` não resultam mais em um <xref:System.NotSupportedException> , pois essas APIs são apoiadas por uma <xref:System.Threading.Tasks.Task> implementação baseada em.

#### <a name="reason-for-change"></a>Motivo da alteração

Alternar a implementação interna do modelo de programação assíncrona (APM) para <xref:System.Threading.Tasks.Task> com base melhora o desempenho e diminui a complexidade do código.

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma ação é necessária na parte do desenvolvedor.

#### <a name="category"></a>Categoria

Rede

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

-->
