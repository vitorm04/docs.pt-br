---
title: Tipo de dados ULong (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ulong
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
- literal type characters, UL
- ULong data type
- UL literal type characters
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
caps.latest.revision: 21
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
ms.openlocfilehash: 4f201189a4573131a1ec1f7554aa460db5a192bb
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="28720-102">Tipo de dados ULong (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28720-102">ULong Data Type (Visual Basic)</span></span>
<span data-ttu-id="28720-103">Contém 64 bits (8 bytes) números inteiros sem sinal que variam em valor entre 0 e 18.446.744.073.709.551.615 (mais do que 1,84 vezes 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="28720-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28720-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="28720-104">Remarks</span></span>  
 <span data-ttu-id="28720-105">Use o `ULong` tipo de dados para armazenar dados binários muito grandes para `UInteger`, ou valores inteiros sem sinal de maior possível.</span><span class="sxs-lookup"><span data-stu-id="28720-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>  
  
 <span data-ttu-id="28720-106">O valor padrão de `ULong` é 0.</span><span class="sxs-lookup"><span data-stu-id="28720-106">The default value of `ULong` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="28720-107">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="28720-107">Programming Tips</span></span>  
  
-   <span data-ttu-id="28720-108">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="28720-108">**Negative Numbers.**</span></span> <span data-ttu-id="28720-109">Porque `ULong` é um tipo sem sinal, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="28720-109">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="28720-110">Se você usar o operador unário menos (`-`) ou uma expressão avaliada como tipo `ULong`, Visual Basic converte a expressão para `Decimal` primeiro.</span><span class="sxs-lookup"><span data-stu-id="28720-110">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>  
  
-   <span data-ttu-id="28720-111">**Compatibilidade com CLS.**</span><span class="sxs-lookup"><span data-stu-id="28720-111">**CLS Compliance.**</span></span> <span data-ttu-id="28720-112">O `ULong` o tipo de dados não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que o utilize.</span><span class="sxs-lookup"><span data-stu-id="28720-112">The `ULong` data type is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="28720-113">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="28720-113">**Interop Considerations.**</span></span> <span data-ttu-id="28720-114">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, tenha em mente que tipos como `ulong` pode ter uma largura de dados diferente (32 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="28720-114">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="28720-115">Se você estiver passando um argumento de 32 bits para tal um componente, declare-o como `UInteger` em vez de `ULong` no seu código Visual Basic gerenciado.</span><span class="sxs-lookup"><span data-stu-id="28720-115">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>  
  
     <span data-ttu-id="28720-116">Além disso, automação não dá suporte a inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="28720-116">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="28720-117">Você não pode passar um Visual Basic `ULong` argumento para um componente de automação dessas plataformas.</span><span class="sxs-lookup"><span data-stu-id="28720-117">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>  
  
-   <span data-ttu-id="28720-118">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="28720-118">**Widening.**</span></span> <span data-ttu-id="28720-119">O `ULong` tipo de dados amplia a `Decimal`, `Single`, e `Double`.</span><span class="sxs-lookup"><span data-stu-id="28720-119">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="28720-120">Isso significa que você pode converter `ULong` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="28720-120">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="28720-121">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="28720-121">**Type Characters.**</span></span> <span data-ttu-id="28720-122">Acrescentar o caractere de tipo literal `UL` a um literal força ao `ULong` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="28720-122">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="28720-123">`ULong`não tem nenhum caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="28720-123">`ULong` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="28720-124">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="28720-124">**Framework Type.**</span></span> <span data-ttu-id="28720-125">O tipo correspondente no .NET Framework é o <xref:System.UInt64?displayProperty=fullName>estrutura.</xref:System.UInt64?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="28720-125">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=fullName> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28720-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28720-126">See Also</span></span>  
 <span data-ttu-id="28720-127"><xref:System.UInt64></xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="28720-127"><xref:System.UInt64></span></span>   
<span data-ttu-id="28720-128"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="28720-128"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="28720-129"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="28720-129"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="28720-130"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="28720-130"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="28720-131"> [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span><span class="sxs-lookup"><span data-stu-id="28720-131"> [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span></span>  
<span data-ttu-id="28720-132"> [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="28720-132"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>
