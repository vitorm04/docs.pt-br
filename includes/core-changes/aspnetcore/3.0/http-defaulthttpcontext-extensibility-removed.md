---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290738"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: Extensibilidade padrãohttpcontext removido

Como parte de ASP.NET melhorias de desempenho do `DefaultHttpContext` Core 3.0, a extensibilidade foi removida. A classe `sealed`é agora. Para obter mais informações, consulte [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).

Se os testes `Mock<DefaultHttpContext>`da `Mock<HttpContext>` `new DefaultHttpContext()` unidade usarem, use ou em vez disso.

Para discussão, consulte [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

As aulas `DefaultHttpContext`podem derivar de .

#### <a name="new-behavior"></a>Novo comportamento

As aulas não `DefaultHttpContext`podem derivar de .

#### <a name="reason-for-change"></a>Motivo da mudança

A extensibilidade foi fornecida inicialmente para `HttpContext`permitir a junção do , mas introduziu complexidade desnecessária e impediu outras otimizações.

#### <a name="recommended-action"></a>Ação recomendada

Se você estiver `Mock<DefaultHttpContext>` usando em seus `Mock<HttpContext>` testes unitários, comece a usar em vez disso.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
