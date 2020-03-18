---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568234"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="90a5e-101">As operações de análise de ponto flutuante não falham mais ou lançam uma Exceção de Estouro</span><span class="sxs-lookup"><span data-stu-id="90a5e-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="90a5e-102">Os métodos de análise de ponto <xref:System.OverflowException> flutuante `false` já não jogam um ou retornam quando analisam <xref:System.Single> uma <xref:System.Double> seqüência cujo valor numérico está fora do alcance do tipo ou ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="90a5e-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="90a5e-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="90a5e-103">Change description</span></span>

<span data-ttu-id="90a5e-104">Em .NET Core 2.2 e <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> versões <xref:System.OverflowException> anteriores, os métodos e os métodos lançam um para valores que estão fora do alcance de seu respectivo tipo.</span><span class="sxs-lookup"><span data-stu-id="90a5e-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="90a5e-105">Os <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> métodos `false` retornam para as representações de string de valores numéricos fora do alcance.</span><span class="sxs-lookup"><span data-stu-id="90a5e-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="90a5e-106">Começando com .NET Core 3.0, <xref:System.Double.Parse%2A?displayProperty=nameWithType>os <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType>métodos e <xref:System.Single.TryParse%2A?displayProperty=nameWithType> métodos não falham mais ao analisar strings numéricas fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="90a5e-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="90a5e-107">Em vez <xref:System.Double> disso, os <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> métodos de <xref:System.Double.MaxValue?displayProperty=nameWithType>análise retornam <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> para valores <xref:System.Double.MinValue?displayProperty=nameWithType>que excedem , e eles retornam para valores inferiores a .</span><span class="sxs-lookup"><span data-stu-id="90a5e-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="90a5e-108">Da mesma <xref:System.Single> forma, os métodos de <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> <xref:System.Single.MaxValue?displayProperty=nameWithType>análise retornam <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> para valores que <xref:System.Single.MinValue?displayProperty=nameWithType>excedem , e eles retornam para valores inferiores a .</span><span class="sxs-lookup"><span data-stu-id="90a5e-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="90a5e-109">Essa mudança foi feita para uma melhor conformidade do IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="90a5e-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="90a5e-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="90a5e-110">Version introduced</span></span>

<span data-ttu-id="90a5e-111">3.0</span><span class="sxs-lookup"><span data-stu-id="90a5e-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="90a5e-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="90a5e-112">Recommended action</span></span>

<span data-ttu-id="90a5e-113">Essa alteração pode afetar seu código de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="90a5e-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="90a5e-114">Seu código depende do manipulador <xref:System.OverflowException> para ser executado quando ocorre um estouro.</span><span class="sxs-lookup"><span data-stu-id="90a5e-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="90a5e-115">Neste caso, você deve `catch` remover a declaração `If` e colocar <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> qualquer <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true`código necessário em uma declaração que teste se ou é .</span><span class="sxs-lookup"><span data-stu-id="90a5e-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="90a5e-116">Seu código pressupõe que os `Infinity`valores de ponto flutuante não são .</span><span class="sxs-lookup"><span data-stu-id="90a5e-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="90a5e-117">Neste caso, você deve adicionar o código necessário para `PositiveInfinity` `NegativeInfinity`verificar se há valores de ponto flutuante de e .</span><span class="sxs-lookup"><span data-stu-id="90a5e-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="90a5e-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="90a5e-118">Category</span></span>

<span data-ttu-id="90a5e-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="90a5e-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="90a5e-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="90a5e-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
