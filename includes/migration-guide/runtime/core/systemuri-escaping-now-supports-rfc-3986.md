---
ms.openlocfilehash: e7001fcfdf88fd9e710fbb702f2ed39d63b1e080
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496733"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a><span data-ttu-id="17afc-101">O escape de System.Uri agora é compatível com RFC 3986</span><span class="sxs-lookup"><span data-stu-id="17afc-101">System.Uri escaping now supports RFC 3986</span></span>

#### <a name="details"></a><span data-ttu-id="17afc-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="17afc-102">Details</span></span>

<span data-ttu-id="17afc-103">O escape do URI foi alterado no .NET Framework 4.5 para atender ao [RFC 3986](https://tools.ietf.org/html/rfc3986).</span><span class="sxs-lookup"><span data-stu-id="17afc-103">URI escaping has changed in .NET Framework 4.5 to support [RFC 3986](https://tools.ietf.org/html/rfc3986).</span></span> <span data-ttu-id="17afc-104">As alterações específicas incluem:</span><span class="sxs-lookup"><span data-stu-id="17afc-104">Specific changes include:</span></span><ul><li><span data-ttu-id="17afc-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> escapa caracteres reservados com base na RFC 3986.</span><span class="sxs-lookup"><span data-stu-id="17afc-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> escapes reserved characters based on RFC 3986.</span></span></li><li><span data-ttu-id="17afc-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> não escapa caracteres reservados.</span><span class="sxs-lookup"><span data-stu-id="17afc-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> does not escape reserved characters.</span></span></li><li><span data-ttu-id="17afc-107"><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> não gerará uma exceção se encontrar uma sequência de escape inválida.</span><span class="sxs-lookup"><span data-stu-id="17afc-107"><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> does not throw an exception if it encounters an invalid escape sequence.</span></span></li><li><span data-ttu-id="17afc-108">Os caracteres escapados não reservados não são escapados.</span><span class="sxs-lookup"><span data-stu-id="17afc-108">Unreserved escaped characters are un-escaped.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="17afc-109">Sugestão</span><span class="sxs-lookup"><span data-stu-id="17afc-109">Suggestion</span></span>

<ul><li><span data-ttu-id="17afc-110">Atualize os aplicativos para não dependerem da geração de <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> no caso de uma sequência de escape inválida.</span><span class="sxs-lookup"><span data-stu-id="17afc-110">Update applications to not rely on <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> to throw in the case of an invalid escape sequence.</span></span> <span data-ttu-id="17afc-111">Essas sequências devem ser detectadas diretamente agora.</span><span class="sxs-lookup"><span data-stu-id="17afc-111">Such sequences must be detected directly now.</span></span></li><li><span data-ttu-id="17afc-112">Da mesma forma, o URI com escape e sem escape, bem como as cadeias de caracteres de dados, podem variar entre o .NET Framework 4.0 e o .NET Framework 4.5 e não devem ser comparados diretamente entre as versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="17afc-112">Similarly, expect that Escaped and Unescaped URI and Data strings may vary from .NET Framework 4.0 and .NET Framework 4.5 and should not be compared across .NET versions directly.</span></span> <span data-ttu-id="17afc-113">Em vez disso, eles devem ser analisados e normalizados em uma única versão do .NET antes que qualquer comparação seja feita.</span><span class="sxs-lookup"><span data-stu-id="17afc-113">Instead, they should be parsed and normalized in a single .NET version before any comparisons are made.</span></span></li></ul>

| <span data-ttu-id="17afc-114">Nome</span><span class="sxs-lookup"><span data-stu-id="17afc-114">Name</span></span>    | <span data-ttu-id="17afc-115">Valor</span><span class="sxs-lookup"><span data-stu-id="17afc-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="17afc-116">Escopo</span><span class="sxs-lookup"><span data-stu-id="17afc-116">Scope</span></span>   |<span data-ttu-id="17afc-117">Secundária</span><span class="sxs-lookup"><span data-stu-id="17afc-117">Minor</span></span>|
|<span data-ttu-id="17afc-118">Versão</span><span class="sxs-lookup"><span data-stu-id="17afc-118">Version</span></span>|<span data-ttu-id="17afc-119">4.5</span><span class="sxs-lookup"><span data-stu-id="17afc-119">4.5</span></span>|
|<span data-ttu-id="17afc-120">Tipo</span><span class="sxs-lookup"><span data-stu-id="17afc-120">Type</span></span>|<span data-ttu-id="17afc-121">Runtime</span><span class="sxs-lookup"><span data-stu-id="17afc-121">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="17afc-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="17afc-122">Affected APIs</span></span>

- <xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType>
- <xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType>
- <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Uri.EscapeDataString(System.String)`
- `M:System.Uri.EscapeUriString(System.String)`
- `M:System.Uri.UnescapeDataString(System.String)`

-->
