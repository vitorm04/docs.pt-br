---
ms.openlocfilehash: 1b4b0aba3ea24682ae972bf283ac387692c83781
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901849"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: extensibilidade defaulthttpcontext removida

Como parte dos aprimoramentos de desempenho do ASP.NET Core 3,0, a extensibilidade do `DefaultHttpContext` foi removida. Agora, a classe é `sealed`. Para obter mais informações, consulte [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).

Se os testes de unidade usarem `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` em vez disso.

Para obter uma discussão, consulte [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).

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
