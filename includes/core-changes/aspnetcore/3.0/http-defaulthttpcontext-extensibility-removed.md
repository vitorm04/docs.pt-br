---
ms.openlocfilehash: 7b5ae84d02b83a10a4b9e002fc2ed4ee0833b84c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198341"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: extensibilidade defaulthttpcontext removida

Como parte dos aprimoramentos de desempenho do ASP.NET Core 3,0, a extensibilidade do `DefaultHttpContext` foi removida. Agora, a classe é `sealed`. Para obter mais informações, consulte [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).

Se os testes de unidade usarem `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` em vez disso.

Para obter uma discussão, consulte [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Classes podem derivar de `DefaultHttpContext`.

#### <a name="new-behavior"></a>Novo comportamento

Classes não podem derivar de `DefaultHttpContext`.

#### <a name="reason-for-change"></a>Motivo da alteração

A extensibilidade foi inicialmente fornecida para permitir o pooling do `HttpContext`, mas introduziu uma complexidade desnecessária e impedia outras otimizações.

#### <a name="recommended-action"></a>Ação recomendada

Se você estiver usando `Mock<DefaultHttpContext>` em seus testes de unidade, comece a usar `Mock<HttpContext>` em vez disso.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
