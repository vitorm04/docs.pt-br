---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721481"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="83865-101">Comportamento de análise e formatação de ponto flutuante alterado</span><span class="sxs-lookup"><span data-stu-id="83865-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="83865-102">A análise de ponto flutuante e o comportamento de formatação (pelos <xref:System.Double> <xref:System.Single> tipos e) agora são compatíveis com IEEE.</span><span class="sxs-lookup"><span data-stu-id="83865-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="83865-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="83865-103">Change description</span></span>

<span data-ttu-id="83865-104">No .NET Core 2,2 e versões anteriores, Formatar com <xref:System.Double.ToString%2A?displayProperty=nameWithType> e e <xref:System.Single.ToString%2A?displayProperty=nameWithType> analisar com <xref:System.Double.Parse%2A?displayProperty=nameWithType> ,, e <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> não são compatíveis com IEEE.</span><span class="sxs-lookup"><span data-stu-id="83865-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="83865-105">Como resultado, é impossível garantir que um valor seja arvoltado com qualquer cadeia de caracteres de formato padrão ou personalizada com suporte.</span><span class="sxs-lookup"><span data-stu-id="83865-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="83865-106">Para algumas entradas, a tentativa de analisar um valor formatado pode falhar e, para outros, o valor analisado não é igual ao valor original.</span><span class="sxs-lookup"><span data-stu-id="83865-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="83865-107">A partir do .NET Core 3,0, as operações de análise e formatação são compatíveis com o IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="83865-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="83865-108">Isso garante que o comportamento dos tipos de ponto flutuante no .NET corresponda ao de linguagens compatíveis com IEEE, como C#.</span><span class="sxs-lookup"><span data-stu-id="83865-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="83865-109">Para obter mais informações, consulte a postagem de [ponto flutuante e melhorias de formatação no blog do .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="83865-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="83865-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83865-110">Version introduced</span></span>

<span data-ttu-id="83865-111">3.0</span><span class="sxs-lookup"><span data-stu-id="83865-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83865-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="83865-112">Recommended action</span></span>

<span data-ttu-id="83865-113">A seção "impacto potencial para código existente" das [melhorias de análise de ponto flutuante e de formatação na](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) postagem de blog do .net Core 3,0 sugere alterações no código se você observar uma alteração de comportamento quando comparada aos aplicativos .net Core 2,2 em geral, isso envolve o uso de uma cadeia de caracteres de formato padrão ou personalizada diferente para impor o comportamento desejado.</span><span class="sxs-lookup"><span data-stu-id="83865-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="83865-114">Alguns resultados podem não ter uma solução alternativa se eles estavam incorretos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="83865-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="83865-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="83865-115">Category</span></span>

<span data-ttu-id="83865-116">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="83865-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83865-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="83865-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
