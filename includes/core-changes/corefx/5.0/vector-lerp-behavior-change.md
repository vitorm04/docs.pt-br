---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281285"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="71037-101">Alteração de comportamento para vector2. Lerp e Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="71037-101">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="71037-102">A implementação de <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> e <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> mudou para uma conta correta para um erro de arredondamento de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="71037-102">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

#### <a name="change-description"></a><span data-ttu-id="71037-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="71037-103">Change description</span></span>

<span data-ttu-id="71037-104">Anteriormente, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> e <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> foram implementados como `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="71037-104">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="71037-105">No entanto, devido a um erro de arredondamento de ponto flutuante, esse algoritmo nem sempre retorna `value2` quando `amount` é `1.0f` .</span><span class="sxs-lookup"><span data-stu-id="71037-105">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="71037-106">No .NET 5,0 e posterior, a implementação usa o mesmo algoritmo que <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> , que é `(value1 * (1.0f - amount)) + (value2 * amount)` .</span><span class="sxs-lookup"><span data-stu-id="71037-106">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="71037-107">Esse algoritmo conta corretamente para o erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="71037-107">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="71037-108">Agora, quando `amount` é `1.0f` , o resultado é precisamente `value2` .</span><span class="sxs-lookup"><span data-stu-id="71037-108">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="71037-109">O algoritmo atualizado também permite que o algoritmo seja otimizado livremente usando <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> quando ele está disponível.</span><span class="sxs-lookup"><span data-stu-id="71037-109">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="71037-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="71037-110">Version introduced</span></span>

<span data-ttu-id="71037-111">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="71037-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="71037-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="71037-112">Recommended action</span></span>

<span data-ttu-id="71037-113">Nenhuma ação é necessária.</span><span class="sxs-lookup"><span data-stu-id="71037-113">No action is necessary.</span></span> <span data-ttu-id="71037-114">No entanto, se você quiser manter o comportamento antigo, poderá implementar sua própria `Lerp` função que usa o algoritmo anterior do `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="71037-114">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

#### <a name="category"></a><span data-ttu-id="71037-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="71037-115">Category</span></span>

<span data-ttu-id="71037-116">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="71037-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="71037-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="71037-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
