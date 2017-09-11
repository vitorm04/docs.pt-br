---
title: Tipo de dados Long (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Long
dev_langs:
- VB
helpviewer_keywords:
- identifier type characters, &
- numbers, whole
- whole numbers
- integral data types
- '& identifier type character'
- integer numbers
- literal type characters, L
- numbers, integer
- integers, data types
- L literal type character
- integers, types
- Long keyword
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
caps.latest.revision: 20
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
ms.openlocfilehash: 17505df1d5f0f4f0312d8d12b8bff50e5274c218
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="a86a8-102">Tipo de dados Long (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a86a8-102">Long Data Type (Visual Basic)</span></span>
<span data-ttu-id="a86a8-103">Armazena inteiros de 64 bits (8 bytes) cujo valor varia de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 (9.2... E + 18).</span><span class="sxs-lookup"><span data-stu-id="a86a8-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a86a8-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a86a8-104">Remarks</span></span>  
 <span data-ttu-id="a86a8-105">Use o `Long` tipo de dados para conter números inteiros que são muito grandes para caber no `Integer` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a86a8-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>  
  
 <span data-ttu-id="a86a8-106">O valor padrão de `Long` é 0.</span><span class="sxs-lookup"><span data-stu-id="a86a8-106">The default value of `Long` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="a86a8-107">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="a86a8-107">Programming Tips</span></span>  
  
-   <span data-ttu-id="a86a8-108">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="a86a8-108">**Interop Considerations.**</span></span> <span data-ttu-id="a86a8-109">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, lembre-se de que `Long` tem uma largura de dados diferente (32 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="a86a8-109">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="a86a8-110">Se você estiver passando um argumento de 32 bits para tal um componente, declare-o como `Integer` em vez de `Long` em seu novo código Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a86a8-110">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>  
  
     <span data-ttu-id="a86a8-111">Além disso, automação não dá suporte a inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="a86a8-111">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="a86a8-112">Você não pode passar um Visual Basic `Long` argumento para um componente de automação nesses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="a86a8-112">You cannot pass a Visual Basic `Long` argument to an Automation component on these operating systems.</span></span>  
  
-   <span data-ttu-id="a86a8-113">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="a86a8-113">**Widening.**</span></span> <span data-ttu-id="a86a8-114">O `Long` tipo de dados amplia a `Decimal`, `Single`, ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="a86a8-114">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="a86a8-115">Isso significa que você pode converter `Long` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a86a8-115">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="a86a8-116">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="a86a8-116">**Type Characters.**</span></span> <span data-ttu-id="a86a8-117">Acrescentar o caractere de tipo literal `L` a um literal o força ao tipo de dados `Long`.</span><span class="sxs-lookup"><span data-stu-id="a86a8-117">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="a86a8-118">Acrescentar o caractere de tipo identificador `&` a qualquer identificador o força ao tipo `Long`.</span><span class="sxs-lookup"><span data-stu-id="a86a8-118">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>  
  
-   <span data-ttu-id="a86a8-119">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="a86a8-119">**Framework Type.**</span></span> <span data-ttu-id="a86a8-120">O tipo correspondente no .NET Framework é o <xref:System.Int64?displayProperty=fullName>estrutura.</xref:System.Int64?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a86a8-120">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=fullName> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a86a8-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a86a8-121">See Also</span></span>  
 <span data-ttu-id="a86a8-122"><xref:System.Int64></xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="a86a8-122"><xref:System.Int64></span></span>   
<span data-ttu-id="a86a8-123"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="a86a8-123"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="a86a8-124"> [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="a86a8-124"> [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="a86a8-125"> [Tipo de dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="a86a8-125"> [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md) </span></span>  
<span data-ttu-id="a86a8-126"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="a86a8-126"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="a86a8-127"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="a86a8-127"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="a86a8-128"> [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="a86a8-128"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>
