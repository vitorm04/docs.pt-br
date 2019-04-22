---
title: Tipo de dados double (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 701d10a334757a96ffd634204c1e1d5eb5418ce6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824657"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="21f96-102">Tipo de dados double (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21f96-102">Double Data Type (Visual Basic)</span></span>
<span data-ttu-id="21f96-103">Mantém conectado IEEE de 64 bits (8 bytes) de precisão dupla números de ponto flutuante que variam em valor de - 1, 79769313486231570E + 308 a - 4.94065645841246544-324 para valores negativos e de 4.94065645841246544-324 1.79769313486231570 + 308 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="21f96-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="21f96-104">Números de precisão dupla armazenam uma aproximação de um número real.</span><span class="sxs-lookup"><span data-stu-id="21f96-104">Double-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21f96-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="21f96-105">Remarks</span></span>  
 <span data-ttu-id="21f96-106">O `Double` tipo de dados fornece o maior e menor magnitude possível para um número.</span><span class="sxs-lookup"><span data-stu-id="21f96-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>  
  
 <span data-ttu-id="21f96-107">O valor padrão de `Double` é 0.</span><span class="sxs-lookup"><span data-stu-id="21f96-107">The default value of `Double` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="21f96-108">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="21f96-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="21f96-109">**Precisão.**</span><span class="sxs-lookup"><span data-stu-id="21f96-109">**Precision.**</span></span> <span data-ttu-id="21f96-110">Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="21f96-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="21f96-111">Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador.</span><span class="sxs-lookup"><span data-stu-id="21f96-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="21f96-112">Para obter mais informações, consulte [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="21f96-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="21f96-113">**Zeros à direita.**</span><span class="sxs-lookup"><span data-stu-id="21f96-113">**Trailing Zeros.**</span></span> <span data-ttu-id="21f96-114">Os tipos de dados de ponto flutuante não possuem uma representação interna de zero caracteres à direita.</span><span class="sxs-lookup"><span data-stu-id="21f96-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="21f96-115">Por exemplo, eles não fazem distinção entre 4,2000 e 4.2.</span><span class="sxs-lookup"><span data-stu-id="21f96-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="21f96-116">Consequentemente, zero caracteres à direita não aparecem quando você exibe ou valores de ponto flutuante de impressão.</span><span class="sxs-lookup"><span data-stu-id="21f96-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="21f96-117">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="21f96-117">**Type Characters.**</span></span> <span data-ttu-id="21f96-118">Acrescentar o caractere de tipo literal `R` a um literal o força ao tipo de dados `Double`.</span><span class="sxs-lookup"><span data-stu-id="21f96-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="21f96-119">Por exemplo, se um valor inteiro é seguido por `R`, o valor é alterado para um `Double`.</span><span class="sxs-lookup"><span data-stu-id="21f96-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     <span data-ttu-id="21f96-120">Acrescentar o caractere de tipo identificador `#` a qualquer identificador o força ao tipo `Double`.</span><span class="sxs-lookup"><span data-stu-id="21f96-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="21f96-121">No exemplo a seguir, a variável `num` é digitada como um `Double`:</span><span class="sxs-lookup"><span data-stu-id="21f96-121">In the following example, the variable `num` is typed as a `Double`:</span></span>  
  
    ```  
    Dim num# = 3  
    ```  
  
-   <span data-ttu-id="21f96-122">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="21f96-122">**Framework Type.**</span></span> <span data-ttu-id="21f96-123">O tipo correspondente no .NET Framework é a estrutura <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21f96-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f96-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21f96-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="21f96-125">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="21f96-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="21f96-126">Tipo de Dados Decimal</span><span class="sxs-lookup"><span data-stu-id="21f96-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="21f96-127">Tipo de Dados Simples</span><span class="sxs-lookup"><span data-stu-id="21f96-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="21f96-128">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="21f96-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="21f96-129">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="21f96-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="21f96-130">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="21f96-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="21f96-131">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="21f96-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="21f96-132">Caracteres de Tipo</span><span class="sxs-lookup"><span data-stu-id="21f96-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
