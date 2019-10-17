---
ms.openlocfilehash: 22ef5d0f91a4f61ca75203f677bcc14e91d77dc1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394078"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: alterações de infraestrutura de corpo de resposta

A infraestrutura que faz o backup de um corpo de resposta HTTP foi alterada. Se você estiver usando `HttpResponse` diretamente, não precisará fazer nenhuma alteração de código. Leia mais detalhadamente se você estiver encapsulando ou substituindo `HttpResponse.Body` ou acessando `HttpContext.Features`.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Havia três APIs associadas ao corpo da resposta HTTP:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Novo comportamento

Se você substituir `HttpResponse.Body`, ele substituirá todo o `IHttpResponseBodyFeature` por um wrapper em seu fluxo específico usando `StreamResponseBodyFeature` para fornecer implementações padrão para todas as APIs esperadas. A configuração de volta do fluxo original reverte essa alteração.

#### <a name="reason-for-change"></a>Motivo da alteração

A motivação é combinar as APIs de corpo de resposta em uma única interface de recurso nova.

#### <a name="recommended-action"></a>Ação recomendada

Use `IHttpResponseBodyFeature` em que você estava usando anteriormente `IHttpResponseFeature.Body`, `IHttpSendFileFeature` ou `IHttpBufferingFeature`.

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
