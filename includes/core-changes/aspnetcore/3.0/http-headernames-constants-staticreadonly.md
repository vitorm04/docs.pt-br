---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394327"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>Constantes HTTP: Headernames alteradas para static readonly

A partir do ASP.NET Core 3,0 Preview 5, os campos em <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> mudaram de `const` para `static readonly`.

Para obter uma discussão, consulte [ASPNET/AspNetCore # 9514](https://github.com/aspnet/AspNetCore/issues/9514).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Esses campos costumava ser `const`.

#### <a name="new-behavior"></a>Novo comportamento

Esses campos agora são `static readonly`.

#### <a name="reason-for-change"></a>Motivo da alteração

A alteração:

* Impede que os valores sejam inseridos entre limites de assembly, permitindo correções de valor conforme necessário.
* Permite verificações de igualdade de referência mais rápidas.

#### <a name="recommended-action"></a>Ação recomendada

Recompile em relação a 3,0. O código-fonte que usa esses campos das seguintes maneiras não pode mais fazer isso:

* Como um argumento de atributo
* Como um `case` em uma instrução `switch`
* Ao definir outro `const`

Para contornar a alteração significativa, alterne para usando constantes de nome de cabeçalho autodefinido ou literais de cadeia de caracteres.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
