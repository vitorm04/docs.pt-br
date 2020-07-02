---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621013"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="21091-101">Categorias do padrão Unicode versão 8.0 agora são compatíveis</span><span class="sxs-lookup"><span data-stu-id="21091-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="21091-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="21091-102">Details</span></span>

<span data-ttu-id="21091-103">No .NET Framework 4.6.2, os dados Unicode foram atualizados do Unicode Standard versão 6.3 para a versão 8.0.</span><span class="sxs-lookup"><span data-stu-id="21091-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="21091-104">Ao solicitar a categorias de caracteres Unicode no .NET Framework 4.6.2, alguns resultados poderão não corresponder aos resultados nas versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21091-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="21091-105">Essa alteração afeta principalmente as sílabas Cheroqui, bem como os símbolos vocálicos e as marcas de tom Tai Lue Novo.</span><span class="sxs-lookup"><span data-stu-id="21091-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="21091-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="21091-106">Suggestion</span></span>

<span data-ttu-id="21091-107">Examine o código e remova ou altere a lógica que depende de categorias de caractere Unicode embutido em código.</span><span class="sxs-lookup"><span data-stu-id="21091-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="21091-108">Name</span><span class="sxs-lookup"><span data-stu-id="21091-108">Name</span></span>    | <span data-ttu-id="21091-109">Valor</span><span class="sxs-lookup"><span data-stu-id="21091-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="21091-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="21091-110">Scope</span></span>   |<span data-ttu-id="21091-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="21091-111">Minor</span></span>|
|<span data-ttu-id="21091-112">Versão</span><span class="sxs-lookup"><span data-stu-id="21091-112">Version</span></span>|<span data-ttu-id="21091-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="21091-113">4.6.2</span></span>|
|<span data-ttu-id="21091-114">Type</span><span class="sxs-lookup"><span data-stu-id="21091-114">Type</span></span>|<span data-ttu-id="21091-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="21091-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="21091-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="21091-116">Affected APIs</span></span>

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
