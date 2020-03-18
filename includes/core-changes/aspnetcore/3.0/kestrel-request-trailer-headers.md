---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394376"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel: Solicitar cabeçalhos de trailer movidos para nova coleção

Em versões anteriores, Kestrel adicionou cabeçalhos de reboque em pedaços HTTP/1.1 na coleção de cabeçalhos de solicitação quando o corpo de solicitação foi lido até o fim. Esse comportamento causou preocupações sobre a ambiguidade entre cabeçalhos e reboques. A decisão foi tomada para mudar os trailers para uma nova coleção.

Os reboques de solicitação HTTP/2 não estavam disponíveis em ASP.NET Core 2.2, mas agora também estão disponíveis nesta nova coleção no ASP.NET Core 3.0.

Novos métodos de extensão de solicitação foram adicionados para acessar esses reboques.

Os reboques HTTP/1.1 estão disponíveis assim que todo o corpo de solicitação tiver sido lido.

Os reboques HTTP/2 estão disponíveis assim que são recebidos do cliente. O cliente não enviará os reboques até que todo o corpo de solicitação tenha sido pelo menos protegido pelo servidor. Você pode precisar ler o corpo de solicitação para liberar espaço de buffer. Os reboques estão sempre disponíveis se você ler o corpo de solicitação até o final. Os trailers marcam a extremidade do corpo.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Solicitar cabeçalhos de `HttpRequest.Headers` reboque seria adicionado à coleção.

#### <a name="new-behavior"></a>Novo comportamento

Os cabeçalhos do trailer `HttpRequest.Headers` não estão **presentes** na coleção. Use os seguintes `HttpRequest` métodos de extensão para acessá-los:

- `GetDeclaredTrailers()`- Recebe o cabeçalho "Trailer" que lista quais reboques esperar após o corpo.
- `SupportsTrailers()`- Indica se a solicitação suporta o recebimento de cabeçalhos de reboque.
- `CheckTrailersAvailable()`- Determina se a solicitação suporta reboques e se eles estão disponíveis para leitura.
- `GetTrailer(string trailerName)`- Recebe o cabeçalho de fuga solicitado da resposta.

#### <a name="reason-for-change"></a>Motivo da mudança

Os trailers são uma característica fundamental em cenários como o gRPC. A fusão dos reboques para solicitar cabeçalhos foi confuso para os usuários.

#### <a name="recommended-action"></a>Ação recomendada

Use os métodos de `HttpRequest` extensão relacionados ao reboque para acessar reboques.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
