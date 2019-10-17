---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394376"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel: Solicitar cabeçalhos de trailer movidos para nova coleção

Nas versões anteriores, Kestrel adicionou cabeçalhos de trailers de HTTP/1.1 na coleção de cabeçalhos de solicitação quando o corpo da solicitação foi lido até o final. Esse comportamento causou preocupações sobre ambigüidade entre cabeçalhos e trailers. A decisão foi feita para mover os trailers para uma nova coleção.

Os trailers de solicitação HTTP/2 não estavam disponíveis no ASP.NET Core 2,2, mas agora também estão disponíveis nesta nova coleção no ASP.NET Core 3,0.

Novos métodos de extensão de solicitação foram adicionados para acessar esses trailers.

Os trailers HTTP/1.1 estão disponíveis quando todo o corpo da solicitação tiver sido lido.

Os trailers HTTP/2 estão disponíveis quando são recebidos do cliente. O cliente não enviará os trailers até que todo o corpo da solicitação tenha sido pelo menos armazenado em buffer pelo servidor. Talvez seja necessário ler o corpo da solicitação para liberar espaço no buffer. Os trailers sempre estarão disponíveis se você ler o corpo da solicitação para o final. Os marcadores marcam o fim do corpo.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Os cabeçalhos do trailer de solicitação seriam adicionados à coleção `HttpRequest.Headers`.

#### <a name="new-behavior"></a>Novo comportamento

Os cabeçalhos de trailer de solicitação **não estão presentes** na coleção `HttpRequest.Headers`. Use os métodos de extensão a seguir em `HttpRequest` para acessá-los:

- `GetDeclaredTrailers()`-Obtém o cabeçalho "trailer" da solicitação que lista os marcadores a serem esperados após o corpo.
- `SupportsTrailers()`-indica se a solicitação dá suporte ao recebimento de cabeçalhos de trailer.
- `CheckTrailersAvailable()`-determina se a solicitação dá suporte a trailers e se está disponível para leitura.
- `GetTrailer(string trailerName)`-Obtém o cabeçalho à direita solicitado da resposta.

#### <a name="reason-for-change"></a>Motivo da alteração

Os trailers são um recurso importante em cenários como o gRPC. Mesclar os trailers em cabeçalhos de solicitação era confuso para os usuários.

#### <a name="recommended-action"></a>Ação recomendada

Use os métodos de extensão relacionados ao trailer em `HttpRequest` para acessar os trailers.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
