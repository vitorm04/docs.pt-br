---
title: Tipo de dados Double (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Double
dev_langs:
- VB
helpviewer_keywords:
- 'identifier type characters, #'
- trailing zeros
- real numbers
- trailing 0 characters
- 0 characters, trailing
- literal type characters, R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers, Double data type
- R literal type character
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 56b97e07489c4abf2ab43a821d9b001518a16aa3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="1a7b1-102">Tipo de dados double (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a7b1-102">Double Data Type (Visual Basic)</span></span>
<span data-ttu-id="1a7b1-103">Mantém assinado IEEE de 64 bits (8 bytes) de precisão dupla números de ponto flutuante que variam em valor entre - 1, 79769313486231570E + 308 até - 4.94065645841246544 e-324 para valores negativos e de 4.94065645841246544 e-324 1.79769313486231570 e + 308 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="1a7b1-104">Números de precisão dupla armazenam uma aproximação de um número real.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-104">Double-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a7b1-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a7b1-105">Remarks</span></span>  
 <span data-ttu-id="1a7b1-106">O `Double` tipo de dados fornece a maior e menor magnitude possível para um número.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>  
  
 <span data-ttu-id="1a7b1-107">O valor padrão de `Double` é 0.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-107">The default value of `Double` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="1a7b1-108">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="1a7b1-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="1a7b1-109">**Precisão.**</span><span class="sxs-lookup"><span data-stu-id="1a7b1-109">**Precision.**</span></span> <span data-ttu-id="1a7b1-110">Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="1a7b1-111">Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="1a7b1-112">Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="1a7b1-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="1a7b1-113">**Os Zeros à direita.**</span><span class="sxs-lookup"><span data-stu-id="1a7b1-113">**Trailing Zeros.**</span></span> <span data-ttu-id="1a7b1-114">Os tipos de dados de ponto flutuante não possuem uma representação interna de zero caracteres à direita.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="1a7b1-115">Por exemplo, eles não fazem distinção entre 4,2000 e 4,2.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="1a7b1-116">Consequentemente, zero caracteres à direita não aparecem quando você exibe ou valores de ponto flutuante de impressão.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="1a7b1-117">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="1a7b1-117">**Type Characters.**</span></span> <span data-ttu-id="1a7b1-118">Acrescentar o caractere de tipo literal `R` a um literal o força ao tipo de dados `Double`.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="1a7b1-119">Por exemplo, se um valor inteiro é seguido por `R`, o valor é alterado para um `Double`.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     <span data-ttu-id="1a7b1-120">Acrescentar o caractere de tipo identificador `#` a qualquer identificador o força ao tipo `Double`.</span><span class="sxs-lookup"><span data-stu-id="1a7b1-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="1a7b1-121">No exemplo a seguir, a variável `num` é digitado como um `Double`:</span><span class="sxs-lookup"><span data-stu-id="1a7b1-121">In the following example, the variable `num` is typed as a `Double`:</span></span>  
  
    ```  
    Dim num# = 3  
    ```  
  
-   <span data-ttu-id="1a7b1-122">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="1a7b1-122">**Framework Type.**</span></span> <span data-ttu-id="1a7b1-123">O tipo correspondente no .NET Framework é o <xref:System.Double?displayProperty=fullName>estrutura.</xref:System.Double?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1a7b1-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=fullName> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a7b1-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a7b1-124">See Also</span></span>  
 <span data-ttu-id="1a7b1-125"><xref:System.Double?displayProperty=fullName></xref:System.Double?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1a7b1-125"><xref:System.Double?displayProperty=fullName></span></span>   
<span data-ttu-id="1a7b1-126"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="1a7b1-126"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="1a7b1-127"> [Tipo de dados decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="1a7b1-127"> [Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md) </span></span>  
<span data-ttu-id="1a7b1-128"> [Tipo de dados Single](../../../visual-basic/language-reference/data-types/single-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="1a7b1-128"> [Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md) </span></span>  
<span data-ttu-id="1a7b1-129"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="1a7b1-129"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="1a7b1-130"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="1a7b1-130"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="1a7b1-131"> [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1a7b1-131"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span></span>  
<span data-ttu-id="1a7b1-132"> [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1a7b1-132"> [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="1a7b1-133"> [Caracteres de Tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span><span class="sxs-lookup"><span data-stu-id="1a7b1-133"> [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span>
