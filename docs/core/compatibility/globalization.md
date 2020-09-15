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
# <a name="globalization-breaking-changes"></a><span data-ttu-id="4a5ce-103">Alterações significativas de globalização</span><span class="sxs-lookup"><span data-stu-id="4a5ce-103">Globalization breaking changes</span></span>

<span data-ttu-id="4a5ce-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="4a5ce-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="4a5ce-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="4a5ce-105">Breaking change</span></span> | <span data-ttu-id="4a5ce-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="4a5ce-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="4a5ce-107">Categoria Unicode alterada para alguns caracteres latinos-1</span><span class="sxs-lookup"><span data-stu-id="4a5ce-107">Unicode category changed for some Latin-1 characters</span></span>](#unicode-category-changed-for-some-latin-1-characters) | <span data-ttu-id="4a5ce-108">5,0</span><span class="sxs-lookup"><span data-stu-id="4a5ce-108">5.0</span></span> |
| [<span data-ttu-id="4a5ce-109">APIs de globalização usam bibliotecas ICU no Windows</span><span class="sxs-lookup"><span data-stu-id="4a5ce-109">Globalization APIs use ICU libraries on Windows</span></span>](#globalization-apis-use-icu-libraries-on-windows) | <span data-ttu-id="4a5ce-110">5,0</span><span class="sxs-lookup"><span data-stu-id="4a5ce-110">5.0</span></span> |
| [<span data-ttu-id="4a5ce-111">StringInfo e TextElementEnumerator agora são compatíveis com UAX29</span><span class="sxs-lookup"><span data-stu-id="4a5ce-111">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | <span data-ttu-id="4a5ce-112">5,0</span><span class="sxs-lookup"><span data-stu-id="4a5ce-112">5.0</span></span> |
| [<span data-ttu-id="4a5ce-113">A localidade "C" é mapeada para a localidade invariável</span><span class="sxs-lookup"><span data-stu-id="4a5ce-113">"C" locale maps to the invariant locale</span></span>](#c-locale-maps-to-the-invariant-locale) | <span data-ttu-id="4a5ce-114">3.0</span><span class="sxs-lookup"><span data-stu-id="4a5ce-114">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="4a5ce-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="4a5ce-115">.NET 5.0</span></span>

[!INCLUDE [unicode-categories-for-latin1-chars](../../../includes/core-changes/globalization/5.0/unicode-categories-for-latin1-chars.md)]

***

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="4a5ce-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4a5ce-116">.NET Core 3.0</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
