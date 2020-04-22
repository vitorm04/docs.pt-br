---
ms.openlocfilehash: 22dbb1e982f83687a9e0eb288ed72c78c676db77
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021628"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="7c0e3-101">O comportamento de formatação e análise de pontos flutuantes mudou</span><span class="sxs-lookup"><span data-stu-id="7c0e3-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="7c0e3-102">O comportamento de análise e formatação <xref:System.Double> <xref:System.Single> de pontos flutuantes (pelos e tipos) agora está em conformidade com o IEEE.</span><span class="sxs-lookup"><span data-stu-id="7c0e3-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7c0e3-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="7c0e3-103">Change description</span></span>

<span data-ttu-id="7c0e3-104">Em .NET Core 2.2 e versões anteriores, formatação <xref:System.Single.Parse%2A?displayProperty=nameWithType>com <xref:System.Single.TryParse%2A?displayProperty=nameWithType> <xref:System.Double.ToString%2A?displayProperty=nameWithType> e <xref:System.Single.ToString%2A?displayProperty=nameWithType>, e parsing com <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, , e não são compatíveis com IEEE.</span><span class="sxs-lookup"><span data-stu-id="7c0e3-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="7c0e3-105">Como resultado, é impossível garantir que um valor irá fazer uma ida e volta com qualquer seqüência de formato padrão ou personalizado suportado.</span><span class="sxs-lookup"><span data-stu-id="7c0e3-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="7c0e3-106">Para algumas entradas, a tentativa de analisar um valor formatado pode falhar, e para outros, o valor analisado não é igual ao valor original.</span><span class="sxs-lookup"><span data-stu-id="7c0e3-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="7c0e3-107">Começando com o .NET Core 3.0, as operações de análise e formatação são compatíveis com o IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="7c0e3-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="7c0e3-108">Isso garante que o comportamento dos tipos de ponto flutuante no .NET corresponda ao de linguagens compatíveis com o IEEE, como C#.</span><span class="sxs-lookup"><span data-stu-id="7c0e3-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="7c0e3-109">Para obter mais informações, consulte as melhorias de análise e formatação de pontos flutuantes no post do blog [.NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)</span><span class="sxs-lookup"><span data-stu-id="7c0e3-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7c0e3-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7c0e3-110">Version introduced</span></span>

<span data-ttu-id="7c0e3-111">3.0</span><span class="sxs-lookup"><span data-stu-id="7c0e3-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7c0e3-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="7c0e3-112">Recommended action</span></span>

<span data-ttu-id="7c0e3-113">A seção "Impacto potencial ao código existente" da análise de ponto flutuante e melhorias de formatação no post do blog [.NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) sugere alterações no seu código se você observar uma mudança de comportamento quando comparado com aplicativos .NET Core 2.2 Geralmente, isso envolve o uso de uma seqüência de formato padrão ou personalizado diferente para impor o comportamento desejado.</span><span class="sxs-lookup"><span data-stu-id="7c0e3-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="7c0e3-114">Alguns resultados podem não ter uma solução se estiverem anteriormente incorretos.</span><span class="sxs-lookup"><span data-stu-id="7c0e3-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="7c0e3-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="7c0e3-115">Category</span></span>

<span data-ttu-id="7c0e3-116">Bibliotecas Core .NET</span><span class="sxs-lookup"><span data-stu-id="7c0e3-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7c0e3-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7c0e3-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
