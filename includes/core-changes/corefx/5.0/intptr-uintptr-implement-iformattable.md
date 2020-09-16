---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024687"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="ab082-101">IntPtr e UIntPtr implementam IFormattable</span><span class="sxs-lookup"><span data-stu-id="ab082-101">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="ab082-102"><xref:System.IntPtr> e <xref:System.UIntPtr> agora implemente <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="ab082-102"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="ab082-103">As funções que verificam o <xref:System.IFormattable> suporte agora podem retornar resultados diferentes para esses tipos, pois eles podem passar um especificador de formato e uma cultura.</span><span class="sxs-lookup"><span data-stu-id="ab082-103">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ab082-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="ab082-104">Change description</span></span>

<span data-ttu-id="ab082-105">Em versões anteriores do .NET, <xref:System.IntPtr> e <xref:System.UIntPtr> não implemente <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="ab082-105">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="ab082-106">As funções que verificam <xref:System.IFormattable> podem retornar a apenas chamar <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> ou <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> , o que significa que especificadores de formato e culturas não são respeitados.</span><span class="sxs-lookup"><span data-stu-id="ab082-106">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="ab082-107">No .NET 5,0 e versões posteriores, <xref:System.IntPtr> e <xref:System.UIntPtr> implemente <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="ab082-107">In .NET 5.0 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="ab082-108">As funções que verificam o <xref:System.IFormattable> suporte agora podem retornar resultados diferentes para esses tipos, pois eles podem passar um especificador de formato e uma cultura.</span><span class="sxs-lookup"><span data-stu-id="ab082-108">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="ab082-109">Essa alteração afeta cenários como cadeias de caracteres interpoladas e <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , entre outros.</span><span class="sxs-lookup"><span data-stu-id="ab082-109">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ab082-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ab082-110">Reason for change</span></span>

<span data-ttu-id="ab082-111"><xref:System.IntPtr> e <xref:System.UIntPtr> agora tem suporte a idiomas em C# por meio das `nint` `nuint` palavras-chave e.</span><span class="sxs-lookup"><span data-stu-id="ab082-111"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="ab082-112">Os tipos de suporte foram atualizados para fornecer paridade próxima (quando possível) com a funcionalidade exposta por outros tipos primitivos, como <xref:System.Int32?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ab082-112">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ab082-113">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ab082-113">Version introduced</span></span>

<span data-ttu-id="ab082-114">5,0 versão prévia 4</span><span class="sxs-lookup"><span data-stu-id="ab082-114">5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ab082-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ab082-115">Recommended action</span></span>

<span data-ttu-id="ab082-116">Se você não quiser que um especificador de formato ou cultura personalizada seja usado ao exibir valores desses tipos, você pode chamar o <xref:System.IntPtr.ToString?displayProperty=nameWithType> e <xref:System.UIntPtr.ToString?displayProperty=nameWithType> sobrecargas de `ToString()` .</span><span class="sxs-lookup"><span data-stu-id="ab082-116">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

#### <a name="category"></a><span data-ttu-id="ab082-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="ab082-117">Category</span></span>

<span data-ttu-id="ab082-118">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="ab082-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ab082-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ab082-119">Affected APIs</span></span>

<span data-ttu-id="ab082-120">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="ab082-120">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
