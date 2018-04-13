---
title: Como converter um objeto em outro tipo no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 053c93e7cf842138f5b9299cd2fcfa56342dd40b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="7f835-102">Como converter um objeto em outro tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7f835-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="7f835-103">Converter um `Object` variável para outro tipo de dados usando uma palavra-chave de conversão, como [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="7f835-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f835-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f835-104">Example</span></span>  
 <span data-ttu-id="7f835-105">O exemplo a seguir converte um `Object` variável para um `Integer` e um `String`.</span><span class="sxs-lookup"><span data-stu-id="7f835-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="7f835-106">Se você souber que o conteúdo de um `Object` variável são de um tipo de dados específico, é melhor converter a variável para esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="7f835-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="7f835-107">Se você continuar a usar o `Object` variável, você provoca uma *boxing* e *unboxing* (para um tipo de valor) ou *associação tardia* (para um tipo de referência).</span><span class="sxs-lookup"><span data-stu-id="7f835-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="7f835-108">Essas operações usam mais tempo de execução e diminuem o desempenho.</span><span class="sxs-lookup"><span data-stu-id="7f835-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f835-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7f835-109">Compiling the Code</span></span>  
 <span data-ttu-id="7f835-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="7f835-110">This example requires:</span></span>  
  
-   <span data-ttu-id="7f835-111">Uma referência para o <xref:System?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="7f835-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f835-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f835-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="7f835-113">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7f835-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="7f835-114">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="7f835-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="7f835-115">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="7f835-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="7f835-116">Conversões entre Cadeias de Caracteres e Outros Tipos</span><span class="sxs-lookup"><span data-stu-id="7f835-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="7f835-117">Conversões de Matriz</span><span class="sxs-lookup"><span data-stu-id="7f835-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="7f835-118">Estruturas</span><span class="sxs-lookup"><span data-stu-id="7f835-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="7f835-119">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="7f835-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="7f835-120">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="7f835-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
