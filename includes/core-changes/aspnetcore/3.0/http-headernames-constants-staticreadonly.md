---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902053"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: CabeçalhosAs constantes alteradas para leitura estática

A partir de ASP.NET O Núcleo 3.0 `const` `static readonly`Preview 5, os campos em <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> mudou de para .

Para discussão, consulte [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Esses campos costumavam ser. `const`

#### <a name="new-behavior"></a>Novo comportamento

Esses campos `static readonly`estão agora.

#### <a name="reason-for-change"></a>Motivo da mudança

A mudança:

* Impede que os valores sejam incorporados através dos limites de montagem, permitindo correções de valor conforme necessário.
* Permite verificações mais rápidas de igualdade de referência.

#### <a name="recommended-action"></a>Ação recomendada

Recompilar contra 3.0. O código-fonte que utiliza esses campos das seguintes maneiras não pode mais fazê-lo:

* Como argumento de atributo
* Como `case` uma `switch` declaração
* Ao definir outro`const`

Para contornar a mudança de quebra, mude para usar constantes de nome de cabeçalho auto-definidas ou literais de seqüência.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
