---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568234"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="ba7f3-101">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="ba7f3-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="ba7f3-102">Os métodos de análise de ponto flutuante não lançam mais um <xref:System.OverflowException> ou retornam `false` quando analisam uma cadeia de caracteres cujo valor numérico está fora do intervalo do <xref:System.Single> ou <xref:System.Double> tipo de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ba7f3-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="ba7f3-103">Change description</span></span>

<span data-ttu-id="ba7f3-104">No .NET Core 2,2 e versões anteriores, os métodos <xref:System.Double.Parse%2A?displayProperty=nameWithType> e <xref:System.Single.Parse%2A?displayProperty=nameWithType> geram uma <xref:System.OverflowException> para valores que estão fora do intervalo de seus respectivos tipos.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="ba7f3-105">Os métodos <xref:System.Double.TryParse%2A?displayProperty=nameWithType> e <xref:System.Single.TryParse%2A?displayProperty=nameWithType> retornam `false` para as representações de cadeia de caracteres de valores numéricos fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="ba7f3-106">A partir do .NET Core 3,0, os métodos <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>e <xref:System.Single.TryParse%2A?displayProperty=nameWithType> não falham mais ao analisar cadeias de caracteres numéricas fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="ba7f3-107">Em vez disso, os métodos de análise de <xref:System.Double> retornam <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> para valores que excedem <xref:System.Double.MaxValue?displayProperty=nameWithType>e retornam <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> para valores menores que <xref:System.Double.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ba7f3-108">Da mesma forma, os métodos de análise de <xref:System.Single> retornam <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> para valores que excedem <xref:System.Single.MaxValue?displayProperty=nameWithType>e retornam <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> para valores menores que <xref:System.Single.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ba7f3-109">Essa alteração foi feita para melhorar a conformidade com o IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ba7f3-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ba7f3-110">Version introduced</span></span>

<span data-ttu-id="ba7f3-111">3.0</span><span class="sxs-lookup"><span data-stu-id="ba7f3-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ba7f3-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ba7f3-112">Recommended action</span></span>

<span data-ttu-id="ba7f3-113">Essa alteração pode afetar o código de uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="ba7f3-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="ba7f3-114">Seu código depende do manipulador para que o <xref:System.OverflowException> seja executado quando ocorrer um estouro.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="ba7f3-115">Nesse caso, você deve remover a instrução `catch` e inserir qualquer código necessário em uma instrução `If` que testa se <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> ou <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> é `true`.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="ba7f3-116">Seu código supõe que os valores de ponto flutuante não são `Infinity`.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="ba7f3-117">Nesse caso, você deve adicionar o código necessário para verificar se há valores de ponto flutuante de `PositiveInfinity` e `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="ba7f3-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="ba7f3-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="ba7f3-118">Category</span></span>

<span data-ttu-id="ba7f3-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="ba7f3-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ba7f3-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ba7f3-120">Affected APIs</span></span>

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
