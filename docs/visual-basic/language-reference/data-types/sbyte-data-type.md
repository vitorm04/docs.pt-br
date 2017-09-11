---
title: Tipo de dados SByte (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.sbyte
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
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
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
ms.openlocfilehash: d8b675dfecfd9f14e7bd5a2113f12a0299caf543
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="acd1d-102">Tipo de dados SByte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acd1d-102">SByte Data Type (Visual Basic)</span></span>
<span data-ttu-id="acd1d-103">Armazena inteiros de 8 bits (1 byte) que variam em valor de -128 a 127.</span><span class="sxs-lookup"><span data-stu-id="acd1d-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acd1d-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="acd1d-104">Remarks</span></span>  
 <span data-ttu-id="acd1d-105">Use o `SByte` tipo de dados para conter valores inteiros que não requerem a largura total de dados de `Integer` ou até mesmo a metade dos bits de `Short`.</span><span class="sxs-lookup"><span data-stu-id="acd1d-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="acd1d-106">Em alguns casos, o common language runtime pode ser possível empacotar sua `SByte` variáveis próximas uma da outra e economizar memória.</span><span class="sxs-lookup"><span data-stu-id="acd1d-106">In some cases the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="acd1d-107">O valor padrão de `SByte` é 0.</span><span class="sxs-lookup"><span data-stu-id="acd1d-107">The default value of `SByte` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="acd1d-108">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="acd1d-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="acd1d-109">**Compatibilidade com CLS.**</span><span class="sxs-lookup"><span data-stu-id="acd1d-109">**CLS Compliance.**</span></span> <span data-ttu-id="acd1d-110">O `SByte` o tipo de dados não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que o utilize.</span><span class="sxs-lookup"><span data-stu-id="acd1d-110">The `SByte` data type is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="acd1d-111">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="acd1d-111">**Widening.**</span></span> <span data-ttu-id="acd1d-112">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span><span class="sxs-lookup"><span data-stu-id="acd1d-112">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="acd1d-113">Isso significa que você pode converter `SByte` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="acd1d-113">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="acd1d-114">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="acd1d-114">**Type Characters.**</span></span> <span data-ttu-id="acd1d-115">`SByte`não possui caractere de tipo literal ou caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="acd1d-115">`SByte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="acd1d-116">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="acd1d-116">**Framework Type.**</span></span> <span data-ttu-id="acd1d-117">O tipo correspondente no .NET Framework é o <xref:System.SByte?displayProperty=fullName>estrutura.</xref:System.SByte?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="acd1d-117">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=fullName> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd1d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acd1d-118">See Also</span></span>  
 <span data-ttu-id="acd1d-119"><xref:System.SByte?displayProperty=fullName></xref:System.SByte?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="acd1d-119"><xref:System.SByte?displayProperty=fullName></span></span>   
<span data-ttu-id="acd1d-120"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="acd1d-120"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="acd1d-121"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="acd1d-121"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="acd1d-122"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="acd1d-122"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="acd1d-123"> [Tipo de dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="acd1d-123"> [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md) </span></span>  
<span data-ttu-id="acd1d-124"> [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="acd1d-124"> [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="acd1d-125"> [Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="acd1d-125"> [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md) </span></span>  
<span data-ttu-id="acd1d-126"> [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="acd1d-126"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>
