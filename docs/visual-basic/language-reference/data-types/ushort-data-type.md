---
title: Tipo de dados UShort (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ushort
dev_langs:
- VB
helpviewer_keywords:
- numbers, whole
- literal type characters, US
- whole numbers
- integral data types
- integer numbers
- numbers, integer
- integers, data types
- integers, types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
caps.latest.revision: 16
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
ms.openlocfilehash: 4f7a36b91a1215eabe7afca1084bee9eb453b037
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="6e545-102">Tipo de dados UShort (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e545-102">UShort Data Type (Visual Basic)</span></span>
<span data-ttu-id="6e545-103">Armazena inteiros sem sinal 16 bits (2 bytes) cujo valor varia de 0 a 65.535.</span><span class="sxs-lookup"><span data-stu-id="6e545-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e545-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e545-104">Remarks</span></span>  
 <span data-ttu-id="6e545-105">Use o `UShort` tipo de dados para armazenar dados binários muito grandes para `Byte`.</span><span class="sxs-lookup"><span data-stu-id="6e545-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="6e545-106">O valor padrão de `UShort` é 0.</span><span class="sxs-lookup"><span data-stu-id="6e545-106">The default value of `UShort` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="6e545-107">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="6e545-107">Programming Tips</span></span>  
  
-   <span data-ttu-id="6e545-108">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="6e545-108">**Negative Numbers.**</span></span> <span data-ttu-id="6e545-109">Porque `UShort` é um tipo sem sinal, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="6e545-109">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="6e545-110">Se você usar o operador unário menos (`-`) ou uma expressão avaliada como tipo `UShort`, Visual Basic converte a expressão para `Integer` primeiro.</span><span class="sxs-lookup"><span data-stu-id="6e545-110">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="6e545-111">**Compatibilidade com CLS.**</span><span class="sxs-lookup"><span data-stu-id="6e545-111">**CLS Compliance.**</span></span> <span data-ttu-id="6e545-112">O `UShort` o tipo de dados não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que o utilize.</span><span class="sxs-lookup"><span data-stu-id="6e545-112">The `UShort` data type is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="6e545-113">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="6e545-113">**Widening.**</span></span> <span data-ttu-id="6e545-114">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span><span class="sxs-lookup"><span data-stu-id="6e545-114">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="6e545-115">Isso significa que você pode converter `UShort` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6e545-115">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="6e545-116">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="6e545-116">**Type Characters.**</span></span> <span data-ttu-id="6e545-117">Acrescentar o caractere de tipo literal `US` a um literal força ao `UShort` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="6e545-117">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="6e545-118">`UShort`não tem nenhum caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="6e545-118">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="6e545-119">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="6e545-119">**Framework Type.**</span></span> <span data-ttu-id="6e545-120">O tipo correspondente no .NET Framework é o <xref:System.UInt16?displayProperty=fullName>estrutura.</xref:System.UInt16?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6e545-120">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=fullName> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e545-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e545-121">See Also</span></span>  
 <span data-ttu-id="6e545-122"><xref:System.UInt16></xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="6e545-122"><xref:System.UInt16></span></span>   
<span data-ttu-id="6e545-123"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="6e545-123"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="6e545-124"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="6e545-124"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="6e545-125"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="6e545-125"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="6e545-126"> [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span><span class="sxs-lookup"><span data-stu-id="6e545-126"> [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span></span>  
<span data-ttu-id="6e545-127"> [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="6e545-127"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>
