---
title: Tipo de dados UInteger | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.uinteger
dev_langs:
- VB
helpviewer_keywords:
- numbers, whole
- UInteger data type
- literal type characters, UI
- whole numbers
- integral data types
- integer numbers
- numbers, integer
- integers, data types
- integers, types
- UI literal type characters
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
caps.latest.revision: 19
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
ms.openlocfilehash: 576a2911f2c7f422ad25f177efa2e8ad20adb7ac
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="uinteger-data-type"></a><span data-ttu-id="4767f-102">Tipo de dados UInteger</span><span class="sxs-lookup"><span data-stu-id="4767f-102">UInteger Data Type</span></span>
<span data-ttu-id="4767f-103">Armazena inteiros sem sinal 32 bits (4 bytes) variando de 0 a 4.294.967.295.</span><span class="sxs-lookup"><span data-stu-id="4767f-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4767f-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="4767f-104">Remarks</span></span>  
 <span data-ttu-id="4767f-105">O `UInteger` tipo de dados fornece o maior valor sem sinal à largura de dados mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="4767f-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="4767f-106">O valor padrão de `UInteger` é 0.</span><span class="sxs-lookup"><span data-stu-id="4767f-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="4767f-107">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="4767f-107">Programming Tips</span></span>  
 <span data-ttu-id="4767f-108">O `UInteger` e `Integer` tipos de dados fornecem um desempenho ideal em um processador de 32 bits, porque os tipos de inteiro menores (`UShort`, `Short`, `Byte`, e `SByte`), mesmo que eles usam menos bits, levará mais tempo para carregar, armazenar e buscar.</span><span class="sxs-lookup"><span data-stu-id="4767f-108">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
-   <span data-ttu-id="4767f-109">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="4767f-109">**Negative Numbers.**</span></span> <span data-ttu-id="4767f-110">Porque `UInteger` é um tipo sem sinal, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="4767f-110">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="4767f-111">Se você usar o operador unário menos (`-`) ou uma expressão avaliada como tipo `UInteger`, Visual Basic converte a expressão para `Long` primeiro.</span><span class="sxs-lookup"><span data-stu-id="4767f-111">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
-   <span data-ttu-id="4767f-112">**Compatibilidade com CLS.**</span><span class="sxs-lookup"><span data-stu-id="4767f-112">**CLS Compliance.**</span></span> <span data-ttu-id="4767f-113">O `UInteger` o tipo de dados não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que o utilize.</span><span class="sxs-lookup"><span data-stu-id="4767f-113">The `UInteger` data type is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="4767f-114">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="4767f-114">**Interop Considerations.**</span></span> <span data-ttu-id="4767f-115">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, tenha em mente que tipos como `uint` pode ter uma largura de dados diferente (16 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="4767f-115">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="4767f-116">Se você estiver passando um argumento de 16 bits para tal um componente, declare-o como `UShort` em vez de `UInteger` no seu código Visual Basic gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4767f-116">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
-   <span data-ttu-id="4767f-117">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="4767f-117">**Widening.**</span></span> <span data-ttu-id="4767f-118">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span><span class="sxs-lookup"><span data-stu-id="4767f-118">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="4767f-119">Isso significa que você pode converter `UInteger` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4767f-119">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="4767f-120">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="4767f-120">**Type Characters.**</span></span> <span data-ttu-id="4767f-121">Acrescentar o caractere de tipo literal `UI` a um literal força ao `UInteger` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="4767f-121">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="4767f-122">`UInteger`não tem nenhum caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="4767f-122">`UInteger` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="4767f-123">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="4767f-123">**Framework Type.**</span></span> <span data-ttu-id="4767f-124">O tipo correspondente no .NET Framework é o <xref:System.UInt32?displayProperty=fullName>estrutura.</xref:System.UInt32?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4767f-124">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=fullName> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4767f-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4767f-125">See Also</span></span>  
 <span data-ttu-id="4767f-126"><xref:System.UInt32></xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="4767f-126"><xref:System.UInt32></span></span>   
<span data-ttu-id="4767f-127"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="4767f-127"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="4767f-128"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="4767f-128"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="4767f-129"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="4767f-129"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="4767f-130"> [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span><span class="sxs-lookup"><span data-stu-id="4767f-130"> [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span></span>  
<span data-ttu-id="4767f-131"> [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="4767f-131"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>
