---
ms.openlocfilehash: c103dff320ae30d02c12ea5c585a47b589da8237
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621033"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a><span data-ttu-id="e7940-101">ContentDisposition DateTimes retorna cadeia de caracteres ligeiramente diferente</span><span class="sxs-lookup"><span data-stu-id="e7940-101">ContentDisposition DateTimes returns slightly different string</span></span>

#### <a name="details"></a><span data-ttu-id="e7940-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e7940-102">Details</span></span>

<span data-ttu-id="e7940-103">As representações de cadeia de caracteres de <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> foram atualizadas, a partir da versão 4.6, para sempre representarem o componente de hora de um <xref:System.DateTime?displayProperty=fullName> com dois dígitos.</span><span class="sxs-lookup"><span data-stu-id="e7940-103">String representations of <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>'s have been updated, beginning in 4.6, to always represent the hour component of a <xref:System.DateTime?displayProperty=fullName> with two digits.</span></span> <span data-ttu-id="e7940-104">Isso está em conformidade com a [RFC822](https://www.ietf.org/rfc/rfc0822.txt) e [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span><span class="sxs-lookup"><span data-stu-id="e7940-104">This is to comply with [RFC822](https://www.ietf.org/rfc/rfc0822.txt) and [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span></span> <span data-ttu-id="e7940-105">Isso faz com que <xref:System.Net.Mime.ContentDisposition.ToString> retorne uma cadeia de caracteres ligeiramente diferente na versão 4.6 em cenários em que um dos elementos de tempo da disposição era anterior a 10:00 AM.</span><span class="sxs-lookup"><span data-stu-id="e7940-105">This causes <xref:System.Net.Mime.ContentDisposition.ToString> to return a slightly different string in 4.6 in scenarios where one of the disposition's time elements was before 10:00 AM.</span></span> <span data-ttu-id="e7940-106">Observe que ContentDispositions, às vezes, são serializados por meio de conversão em cadeias de caracteres, de modo que quaisquer operações <xref:System.Net.Mime.ContentDisposition.ToString>, serialização ou chamadas GetHashCode devem ser revisadas.</span><span class="sxs-lookup"><span data-stu-id="e7940-106">Note that ContentDispositions are sometimes serialized via converting them to strings, so any <xref:System.Net.Mime.ContentDisposition.ToString> operations, serialization, or GetHashCode calls should be reviewed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e7940-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e7940-107">Suggestion</span></span>

<span data-ttu-id="e7940-108">Não espere que essas representações de cadeia de caracteres de ContentDispositions de diferentes versões do .NET Framework sejam corretamente comparadas umas com as outras.</span><span class="sxs-lookup"><span data-stu-id="e7940-108">Do not expect that string representations of ContentDispositions from different .NET Framework versions will correctly compare to one another.</span></span> <span data-ttu-id="e7940-109">Converta as cadeias de caracteres de volta em ContentDispositions, se possível, antes de realizar uma comparação.</span><span class="sxs-lookup"><span data-stu-id="e7940-109">Convert the strings back to ContentDispositions, if possible, before conducting a comparison.</span></span>

| <span data-ttu-id="e7940-110">Name</span><span class="sxs-lookup"><span data-stu-id="e7940-110">Name</span></span>    | <span data-ttu-id="e7940-111">Valor</span><span class="sxs-lookup"><span data-stu-id="e7940-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e7940-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="e7940-112">Scope</span></span>   |<span data-ttu-id="e7940-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="e7940-113">Minor</span></span>|
|<span data-ttu-id="e7940-114">Versão</span><span class="sxs-lookup"><span data-stu-id="e7940-114">Version</span></span>|<span data-ttu-id="e7940-115">4.6</span><span class="sxs-lookup"><span data-stu-id="e7940-115">4.6</span></span>|
|<span data-ttu-id="e7940-116">Type</span><span class="sxs-lookup"><span data-stu-id="e7940-116">Type</span></span>|<span data-ttu-id="e7940-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="e7940-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7940-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e7940-118">Affected APIs</span></span>

-<xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
