---
title: "Um único tipo de dados (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Single
dev_langs:
- VB
helpviewer_keywords:
- Single data type
- F literal type character
- trailing zeros
- real numbers
- literal type characters, F
- trailing 0 characters
- identifier type characters, !
- single-precision numbers
- '! identifier type character'
- 0 characters, trailing
- data types [Visual Basic], assigning
- floating-point numbers, Single data type
- numbers, real
- zeros, trailing
- numbers, floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
caps.latest.revision: 15
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
ms.openlocfilehash: 5d8c7e5a0247aed8388a5e1345dc3033e997fdee
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="81b5c-102">Tipo de dados único (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81b5c-102">Single Data Type (Visual Basic)</span></span>
<span data-ttu-id="81b5c-103">Mantém assinado IEEE de 32 bits (4 bytes) de precisão simples números de ponto flutuante cujo valor varia de - 3, 4028235E + 38 até - 1.401298-45 para valores negativos e de 1, 401298E-45 a 3, 4028235E + 38 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="81b5c-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="81b5c-104">Números de precisão simples armazenam uma aproximação de um número real.</span><span class="sxs-lookup"><span data-stu-id="81b5c-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81b5c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="81b5c-105">Remarks</span></span>  
 <span data-ttu-id="81b5c-106">Use o `Single` tipo de dados para armazenar valores inteiros que não requerem a largura total de dados de `Double`.</span><span class="sxs-lookup"><span data-stu-id="81b5c-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="81b5c-107">Em alguns casos, o common language runtime pode ser possível empacotar sua `Single` variáveis próximas uma da outra e economizar memória.</span><span class="sxs-lookup"><span data-stu-id="81b5c-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="81b5c-108">O valor padrão de `Single` é 0.</span><span class="sxs-lookup"><span data-stu-id="81b5c-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="81b5c-109">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="81b5c-109">Programming Tips</span></span>  
  
-   <span data-ttu-id="81b5c-110">**Precisão.**</span><span class="sxs-lookup"><span data-stu-id="81b5c-110">**Precision.**</span></span> <span data-ttu-id="81b5c-111">Quando você trabalha com números de ponto flutuante, tenha em mente que eles nem sempre têm uma representação precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="81b5c-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="81b5c-112">Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador.</span><span class="sxs-lookup"><span data-stu-id="81b5c-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="81b5c-113">Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="81b5c-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="81b5c-114">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="81b5c-114">**Widening.**</span></span> <span data-ttu-id="81b5c-115">O `Single` tipo de dados amplia a `Double`.</span><span class="sxs-lookup"><span data-stu-id="81b5c-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="81b5c-116">Isso significa que você pode converter `Single` para `Double` sem encontrar uma <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="81b5c-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="81b5c-117">**Os Zeros à direita.**</span><span class="sxs-lookup"><span data-stu-id="81b5c-117">**Trailing Zeros.**</span></span> <span data-ttu-id="81b5c-118">Os tipos de dados de ponto flutuante não possuem uma representação interna de 0 caracteres à direita.</span><span class="sxs-lookup"><span data-stu-id="81b5c-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="81b5c-119">Por exemplo, eles não fazem distinção entre 4,2000 e 4,2.</span><span class="sxs-lookup"><span data-stu-id="81b5c-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="81b5c-120">Consequentemente, 0 caracteres à direita não aparecem quando você exibe ou imprime valores de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="81b5c-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="81b5c-121">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="81b5c-121">**Type Characters.**</span></span> <span data-ttu-id="81b5c-122">Acrescentar o caractere de tipo literal `F` a um literal o força ao tipo de dados `Single`.</span><span class="sxs-lookup"><span data-stu-id="81b5c-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="81b5c-123">Acrescentar o caractere de tipo identificador `!` a qualquer identificador o força ao tipo `Single`.</span><span class="sxs-lookup"><span data-stu-id="81b5c-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
-   <span data-ttu-id="81b5c-124">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="81b5c-124">**Framework Type.**</span></span> <span data-ttu-id="81b5c-125">O tipo correspondente no .NET Framework é o <xref:System.Single?displayProperty=fullName>estrutura.</xref:System.Single?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="81b5c-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=fullName> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81b5c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81b5c-126">See Also</span></span>  
 <span data-ttu-id="81b5c-127"><xref:System.Single?displayProperty=fullName></xref:System.Single?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="81b5c-127"><xref:System.Single?displayProperty=fullName></span></span>   
<span data-ttu-id="81b5c-128"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="81b5c-128"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="81b5c-129"> [Tipo de dados decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="81b5c-129"> [Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md) </span></span>  
<span data-ttu-id="81b5c-130"> [Tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="81b5c-130"> [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md) </span></span>  
<span data-ttu-id="81b5c-131"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="81b5c-131"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="81b5c-132"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="81b5c-132"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="81b5c-133"> [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="81b5c-133"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span></span>  
<span data-ttu-id="81b5c-134"> [Solução de problemas de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="81b5c-134"> [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)</span></span>
