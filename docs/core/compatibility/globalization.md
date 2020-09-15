---
title: Alterações significativas de globalização
description: Lista as alterações significativas na globalização no .NET Core.
ms.date: 04/07/2020
ms.openlocfilehash: 93990d89204df1b2d7498e1d748378fae05598c3
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065053"
---
# <a name="globalization-breaking-changes"></a>Alterações significativas de globalização

As seguintes alterações significativas estão documentadas nesta página:

| Alteração significativa | Versão introduzida |
| - | :-: |
| [Categoria Unicode alterada para alguns caracteres latinos-1](#unicode-category-changed-for-some-latin-1-characters) | 5,0 |
| [APIs de globalização usam bibliotecas ICU no Windows](#globalization-apis-use-icu-libraries-on-windows) | 5,0 |
| [StringInfo e TextElementEnumerator agora são compatíveis com UAX29](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | 5,0 |
| [A localidade "C" é mapeada para a localidade invariável](#c-locale-maps-to-the-invariant-locale) | 3.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [unicode-categories-for-latin1-chars](../../../includes/core-changes/globalization/5.0/unicode-categories-for-latin1-chars.md)]

***

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
