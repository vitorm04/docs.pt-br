---
ms.openlocfilehash: f389a9e9bcf4ac1777db66731a085d74889c4a98
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497193"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="e1c79-101">Categorias do padrão Unicode versão 8.0 agora são compatíveis</span><span class="sxs-lookup"><span data-stu-id="e1c79-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="e1c79-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e1c79-102">Details</span></span>

<span data-ttu-id="e1c79-103">No .NET Framework 4.6.2, os dados Unicode foram atualizados do Unicode Standard versão 6.3 para a versão 8.0.</span><span class="sxs-lookup"><span data-stu-id="e1c79-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="e1c79-104">Ao solicitar a categorias de caracteres Unicode no .NET Framework 4.6.2, alguns resultados poderão não corresponder aos resultados nas versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1c79-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="e1c79-105">Essa alteração afeta principalmente as sílabas Cheroqui, bem como os símbolos vocálicos e as marcas de tom Tai Lue Novo.</span><span class="sxs-lookup"><span data-stu-id="e1c79-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e1c79-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e1c79-106">Suggestion</span></span>

<span data-ttu-id="e1c79-107">Examine o código e remova ou altere a lógica que depende de categorias de caractere Unicode embutido em código.</span><span class="sxs-lookup"><span data-stu-id="e1c79-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="e1c79-108">Nome</span><span class="sxs-lookup"><span data-stu-id="e1c79-108">Name</span></span>    | <span data-ttu-id="e1c79-109">Valor</span><span class="sxs-lookup"><span data-stu-id="e1c79-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e1c79-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="e1c79-110">Scope</span></span>   |<span data-ttu-id="e1c79-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="e1c79-111">Minor</span></span>|
|<span data-ttu-id="e1c79-112">Versão</span><span class="sxs-lookup"><span data-stu-id="e1c79-112">Version</span></span>|<span data-ttu-id="e1c79-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e1c79-113">4.6.2</span></span>|
|<span data-ttu-id="e1c79-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="e1c79-114">Type</span></span>|<span data-ttu-id="e1c79-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="e1c79-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e1c79-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e1c79-116">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Char.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)`

-->
