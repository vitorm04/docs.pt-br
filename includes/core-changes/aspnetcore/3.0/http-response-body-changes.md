---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198334"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: Mudanças na infra-estrutura do corpo de resposta

A infra-estrutura que apoia um corpo de resposta HTTP mudou. Se você está `HttpResponse` usando diretamente, você não deve precisar fazer nenhuma alteração de código. Leia mais se você está `HttpResponse.Body` embrulhando `HttpContext.Features`ou substituindo ou acessando .

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Havia três APIs associadas ao corpo de resposta HTTP:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Novo comportamento

Se você `HttpResponse.Body`substituir, ele `IHttpResponseBodyFeature` substituirá o inteiro por `StreamResponseBodyFeature` um invólucro em torno de seu fluxo determinado usando para fornecer implementações padrão para todas as APIs esperadas. A configuração do fluxo original reverte essa alteração.

#### <a name="reason-for-change"></a>Motivo da mudança

A motivação é combinar as APIs do corpo de resposta em uma única interface de recurso novo.

#### <a name="recommended-action"></a>Ação recomendada

Use `IHttpResponseBodyFeature` onde você estava `IHttpResponseFeature.Body` `IHttpSendFileFeature`usando `IHttpBufferingFeature`anteriormente, ou .

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
