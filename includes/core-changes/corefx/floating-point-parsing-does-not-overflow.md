---
ms.openlocfilehash: 192873aa5069aa4f96a18716afb066c80b223e29
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002453"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="b36e9-101">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="b36e9-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="b36e9-102">Os métodos de análise de ponto flutuante não lançam mais um <xref:System.OverflowException> ou retornam `false` quando analisam uma cadeia de caracteres cujo valor numérico está fora do intervalo do tipo de ponto flutuante <xref:System.Single> ou <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="b36e9-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b36e9-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="b36e9-103">Change description</span></span>

<span data-ttu-id="b36e9-104">No .NET Core 2,2 e em versões anteriores, os métodos <xref:System.Double.Parse%2A?displayProperty=nameWithType> e <xref:System.Single.Parse%2A?displayProperty=nameWithType> lançam um <xref:System.OverflowException> para valores que estão fora do intervalo de seus respectivos tipos.</span><span class="sxs-lookup"><span data-stu-id="b36e9-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="b36e9-105">Os métodos <xref:System.Double.TryParse%2A?displayProperty=nameWithType> e <xref:System.Single.TryParse%2A?displayProperty=nameWithType> retornam `false` para as representações de cadeia de caracteres de valores numéricos fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="b36e9-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="b36e9-106">A partir do .NET Core 3,0, os métodos <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType> e <xref:System.Single.TryParse%2A?displayProperty=nameWithType> não falham mais ao analisar cadeias de caracteres numéricas fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="b36e9-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="b36e9-107">Em vez disso, os métodos de análise <xref:System.Double> retornam <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> para valores que excedem <xref:System.Double.MaxValue?displayProperty=nameWithType> e retornam <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> para valores menores que <xref:System.Double.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b36e9-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b36e9-108">Da mesma forma, os métodos de análise <xref:System.Single> retornam <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> para valores que excedem <xref:System.Single.MaxValue?displayProperty=nameWithType> e retornam <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> para valores menores que <xref:System.Single.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b36e9-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b36e9-109">Essa alteração foi feita para melhorar a conformidade com o IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="b36e9-109">This change was made for improved IEEE 754:2008 compliance.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="b36e9-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b36e9-110">Version introduced</span></span>

<span data-ttu-id="b36e9-111">3.0</span><span class="sxs-lookup"><span data-stu-id="b36e9-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b36e9-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b36e9-112">Recommended action</span></span>

<span data-ttu-id="b36e9-113">Essa alteração pode afetar o código de uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="b36e9-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="b36e9-114">Seu código depende do manipulador para que o <xref:System.OverflowException> seja executado quando ocorrer um estouro.</span><span class="sxs-lookup"><span data-stu-id="b36e9-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="b36e9-115">Nesse caso, você deve remover a instrução `catch` e inserir qualquer código necessário em uma instrução `If` que testa se <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> ou <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> é `true`.</span><span class="sxs-lookup"><span data-stu-id="b36e9-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="b36e9-116">Seu código supõe que os valores de ponto flutuante não são `Infinity`.</span><span class="sxs-lookup"><span data-stu-id="b36e9-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="b36e9-117">Nesse caso, você deve adicionar o código necessário para verificar valores de ponto flutuante de `PositiveInfinity` e `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="b36e9-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="b36e9-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="b36e9-118">Category</span></span>

<span data-ttu-id="b36e9-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="b36e9-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b36e9-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b36e9-120">Affected APIs</span></span>

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
