---
title: Tipo de Dados Simples
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
ms.openlocfilehash: ecb0f5f6416a2dd4ddd6888cb80ed3ac11ee58df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415525"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="64ba5-102">Tipo de dados único (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64ba5-102">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="64ba5-103">Contém números de ponto flutuante de precisão simples IEEE 32 bits (4 bytes) que variam em valor de-3.4028235 E + 38 a-1.401298 E-45 para valores negativos e de 1.401298 E-45 a 3.4028235 E + 38 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="64ba5-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="64ba5-104">Números de precisão única armazenam uma aproximação de um número real.</span><span class="sxs-lookup"><span data-stu-id="64ba5-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64ba5-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="64ba5-105">Remarks</span></span>  

 <span data-ttu-id="64ba5-106">Use o `Single` tipo de dados para conter valores de ponto flutuante que não exigem a largura de dados completa de `Double` .</span><span class="sxs-lookup"><span data-stu-id="64ba5-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="64ba5-107">Em alguns casos, a Common Language Runtime pode ser capaz de empacotar suas `Single` variáveis em conjunto e economizar o consumo de memória.</span><span class="sxs-lookup"><span data-stu-id="64ba5-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="64ba5-108">O valor padrão de `Single` é 0.</span><span class="sxs-lookup"><span data-stu-id="64ba5-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="64ba5-109">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="64ba5-109">Programming Tips</span></span>  
  
- <span data-ttu-id="64ba5-110">**Preciso.**</span><span class="sxs-lookup"><span data-stu-id="64ba5-110">**Precision.**</span></span> <span data-ttu-id="64ba5-111">Quando você trabalha com números de ponto flutuante, tenha em mente que eles nem sempre têm uma representação precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="64ba5-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="64ba5-112">Isso pode levar a resultados inesperados de determinadas operações, como comparação de valor e o `Mod` operador.</span><span class="sxs-lookup"><span data-stu-id="64ba5-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="64ba5-113">Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="64ba5-113">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="64ba5-114">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="64ba5-114">**Widening.**</span></span> <span data-ttu-id="64ba5-115">O `Single` tipo de dados amplia para `Double` .</span><span class="sxs-lookup"><span data-stu-id="64ba5-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="64ba5-116">Isso significa que você pode converter `Single` para `Double` sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="64ba5-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="64ba5-117">**Zeros à direita.**</span><span class="sxs-lookup"><span data-stu-id="64ba5-117">**Trailing Zeros.**</span></span> <span data-ttu-id="64ba5-118">Os tipos de dados de ponto flutuante não têm nenhuma representação interna de zero caracteres à direita.</span><span class="sxs-lookup"><span data-stu-id="64ba5-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="64ba5-119">Por exemplo, eles não fazem distinção entre 4,2000 e 4,2.</span><span class="sxs-lookup"><span data-stu-id="64ba5-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="64ba5-120">Consequentemente, 0 caracteres à direita não aparecem quando você exibe ou imprime valores de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="64ba5-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="64ba5-121">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="64ba5-121">**Type Characters.**</span></span> <span data-ttu-id="64ba5-122">Acrescentar o caractere de tipo literal `F` a um literal o força ao tipo de dados `Single`.</span><span class="sxs-lookup"><span data-stu-id="64ba5-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="64ba5-123">Acrescentar o caractere de tipo identificador `!` a qualquer identificador o força ao tipo `Single`.</span><span class="sxs-lookup"><span data-stu-id="64ba5-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="64ba5-124">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="64ba5-124">**Framework Type.**</span></span> <span data-ttu-id="64ba5-125">O tipo correspondente no .NET Framework é a estrutura <xref:System.Single?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="64ba5-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ba5-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="64ba5-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="64ba5-127">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="64ba5-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="64ba5-128">Tipo de Dados Decimal</span><span class="sxs-lookup"><span data-stu-id="64ba5-128">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="64ba5-129">Tipo de Dados Duplo</span><span class="sxs-lookup"><span data-stu-id="64ba5-129">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="64ba5-130">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="64ba5-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="64ba5-131">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="64ba5-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="64ba5-132">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="64ba5-132">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="64ba5-133">Solução de problemas de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="64ba5-133">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
