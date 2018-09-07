---
title: Tipo de dados único (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 98433c0f1d1008664bb994f3b43fe48a753a432c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097903"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="5ad21-102">Tipo de dados único (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ad21-102">Single Data Type (Visual Basic)</span></span>
<span data-ttu-id="5ad21-103">Mantém conectado IEEE de 32 bits (4 bytes) de precisão simples números de ponto flutuante que variam em valor de - 3,4028235E + 38 a - 1,401298E-45 para valores negativos e de 1,401298E-45 3,4028235E + 38 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="5ad21-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="5ad21-104">Números de precisão simples armazenam uma aproximação de um número real.</span><span class="sxs-lookup"><span data-stu-id="5ad21-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ad21-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ad21-105">Remarks</span></span>  
 <span data-ttu-id="5ad21-106">Use o `Single` tipo de dados para conter os valores de ponto flutuante que não exigem a largura de dados completo do `Double`.</span><span class="sxs-lookup"><span data-stu-id="5ad21-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="5ad21-107">Em alguns casos, o common language runtime pode ser capaz de empacotar seu `Single` variáveis próximas uma da outra e economizar memória.</span><span class="sxs-lookup"><span data-stu-id="5ad21-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="5ad21-108">O valor padrão de `Single` é 0.</span><span class="sxs-lookup"><span data-stu-id="5ad21-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="5ad21-109">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="5ad21-109">Programming Tips</span></span>  
  
-   <span data-ttu-id="5ad21-110">**Precisão.**</span><span class="sxs-lookup"><span data-stu-id="5ad21-110">**Precision.**</span></span> <span data-ttu-id="5ad21-111">Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="5ad21-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="5ad21-112">Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador.</span><span class="sxs-lookup"><span data-stu-id="5ad21-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="5ad21-113">Para obter mais informações, consulte [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="5ad21-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="5ad21-114">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="5ad21-114">**Widening.**</span></span> <span data-ttu-id="5ad21-115">O `Single` tipo de dados é ampliado para `Double`.</span><span class="sxs-lookup"><span data-stu-id="5ad21-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="5ad21-116">Isso significa que você pode converter `Single` à `Double` sem encontrar uma <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="5ad21-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="5ad21-117">**Zeros à direita.**</span><span class="sxs-lookup"><span data-stu-id="5ad21-117">**Trailing Zeros.**</span></span> <span data-ttu-id="5ad21-118">Os tipos de dados de ponto flutuante não possuem uma representação interna de 0 caracteres à direita.</span><span class="sxs-lookup"><span data-stu-id="5ad21-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="5ad21-119">Por exemplo, eles não fazem distinção entre 4,2000 e 4.2.</span><span class="sxs-lookup"><span data-stu-id="5ad21-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="5ad21-120">Consequentemente, 0 caracteres à direita não aparecem quando você exibe ou imprimir valores de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="5ad21-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="5ad21-121">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="5ad21-121">**Type Characters.**</span></span> <span data-ttu-id="5ad21-122">Acrescentar o caractere de tipo literal `F` a um literal o força ao tipo de dados `Single`.</span><span class="sxs-lookup"><span data-stu-id="5ad21-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="5ad21-123">Acrescentar o caractere de tipo identificador `!` a qualquer identificador o força ao tipo `Single`.</span><span class="sxs-lookup"><span data-stu-id="5ad21-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
-   <span data-ttu-id="5ad21-124">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="5ad21-124">**Framework Type.**</span></span> <span data-ttu-id="5ad21-125">O tipo correspondente no .NET Framework é a estrutura <xref:System.Single?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ad21-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad21-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ad21-126">See Also</span></span>  
 <xref:System.Single?displayProperty=nameWithType>  
 [<span data-ttu-id="5ad21-127">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="5ad21-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="5ad21-128">Tipo de Dados Decimal</span><span class="sxs-lookup"><span data-stu-id="5ad21-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="5ad21-129">Tipo de Dados Duplo</span><span class="sxs-lookup"><span data-stu-id="5ad21-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="5ad21-130">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="5ad21-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="5ad21-131">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="5ad21-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="5ad21-132">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="5ad21-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="5ad21-133">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="5ad21-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
