---
title: 'Como: converter um objeto em outro tipo no Visual Basic | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
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
ms.openlocfilehash: 9aea63727532174fa1bbb1f9093fbf7c4934bd24
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="0567e-102">Como converter um objeto em outro tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0567e-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="0567e-103">Converter um `Object` variável em outro tipo de dados usando uma palavra-chave de conversão, como [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="0567e-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0567e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0567e-104">Example</span></span>  
 <span data-ttu-id="0567e-105">O exemplo a seguir converte um `Object` variável para um `Integer` e um `String`.</span><span class="sxs-lookup"><span data-stu-id="0567e-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="0567e-106">Se você souber que o conteúdo de um `Object` variável são de um tipo de dados específico, é melhor converter a variável para esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="0567e-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="0567e-107">Se você continuar a usar o `Object` variável, você provoca uma *conversão boxing* e *unboxing* (para um tipo de valor) ou *ligação tardia* (para um tipo de referência).</span><span class="sxs-lookup"><span data-stu-id="0567e-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="0567e-108">Essas operações usam mais tempo de execução e diminuem o desempenho.</span><span class="sxs-lookup"><span data-stu-id="0567e-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0567e-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0567e-109">Compiling the Code</span></span>  
 <span data-ttu-id="0567e-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="0567e-110">This example requires:</span></span>  
  
-   <span data-ttu-id="0567e-111">Uma referência para o <xref:System?displayProperty=fullName>namespace.</xref:System?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0567e-111">A reference to the <xref:System?displayProperty=fullName> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0567e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0567e-112">See Also</span></span>  
 <span data-ttu-id="0567e-113"><xref:System.Object></xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0567e-113"><xref:System.Object></span></span>   
<span data-ttu-id="0567e-114"> [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="0567e-114"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="0567e-115"> [Conversões entre](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="0567e-115"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="0567e-116"> [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="0567e-116"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="0567e-117"> [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md) </span><span class="sxs-lookup"><span data-stu-id="0567e-117"> [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md) </span></span>  
<span data-ttu-id="0567e-118"> [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="0567e-118"> [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span></span>  
<span data-ttu-id="0567e-119"> [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="0567e-119"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="0567e-120"> [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="0567e-120"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="0567e-121"> [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)</span><span class="sxs-lookup"><span data-stu-id="0567e-121"> [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)</span></span>
