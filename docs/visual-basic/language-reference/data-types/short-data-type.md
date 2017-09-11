---
title: Curta o tipo de dados (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Short
dev_langs:
- VB
helpviewer_keywords:
- numbers, whole
- whole numbers
- integral data types
- integer numbers
- numbers, integer
- integers, data types
- integers, types
- data types [Visual Basic], integral
- S literal type character
- Short data type
- literal type characters, S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
caps.latest.revision: 18
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
ms.openlocfilehash: 9764a00d8e2ed555d1dea93326d4bf4860a12ad9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="b45b9-102">Tipo de dados curto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b45b9-102">Short Data Type (Visual Basic)</span></span>
<span data-ttu-id="b45b9-103">Armazena inteiros de 16 bits (2 bytes) que variam de -32.768 a 32.767.</span><span class="sxs-lookup"><span data-stu-id="b45b9-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b45b9-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="b45b9-104">Remarks</span></span>  
 <span data-ttu-id="b45b9-105">Use o `Short` tipo de dados para conter valores inteiros que não requerem a largura total de dados de `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b45b9-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="b45b9-106">Em alguns casos, o common language runtime pode empacotar seu `Short` variáveis próximas uma da outra e economizar memória.</span><span class="sxs-lookup"><span data-stu-id="b45b9-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="b45b9-107">O valor padrão de `Short` é 0.</span><span class="sxs-lookup"><span data-stu-id="b45b9-107">The default value of `Short` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="b45b9-108">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="b45b9-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="b45b9-109">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="b45b9-109">**Widening.**</span></span> <span data-ttu-id="b45b9-110">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span><span class="sxs-lookup"><span data-stu-id="b45b9-110">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="b45b9-111">Isso significa que você pode converter `Short` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b45b9-111">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="b45b9-112">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="b45b9-112">**Type Characters.**</span></span> <span data-ttu-id="b45b9-113">Acrescentar o caractere de tipo literal `S` a um literal o força ao tipo de dados `Short`.</span><span class="sxs-lookup"><span data-stu-id="b45b9-113">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="b45b9-114">`Short`não tem nenhum caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="b45b9-114">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="b45b9-115">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="b45b9-115">**Framework Type.**</span></span> <span data-ttu-id="b45b9-116">O tipo correspondente no .NET Framework é o <xref:System.Int16?displayProperty=fullName>estrutura.</xref:System.Int16?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b45b9-116">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=fullName> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45b9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b45b9-117">See Also</span></span>  
 <span data-ttu-id="b45b9-118"><xref:System.Int16?displayProperty=fullName></xref:System.Int16?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b45b9-118"><xref:System.Int16?displayProperty=fullName></span></span>   
<span data-ttu-id="b45b9-119"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="b45b9-119"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="b45b9-120"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="b45b9-120"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="b45b9-121"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="b45b9-121"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="b45b9-122"> [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="b45b9-122"> [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="b45b9-123"> [Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="b45b9-123"> [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md) </span></span>  
<span data-ttu-id="b45b9-124"> [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="b45b9-124"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>
