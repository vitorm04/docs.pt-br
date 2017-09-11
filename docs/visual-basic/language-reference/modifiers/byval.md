---
title: ByVal (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
dev_langs:
- VB
helpviewer_keywords:
- ByVal keyword, contexts
- ByVal keyword
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: 14
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
ms.openlocfilehash: febc8dca3f4513ccc240bb5b29def92ecdf73cbc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="byval-visual-basic"></a><span data-ttu-id="998d3-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="998d3-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="998d3-103">Especifica que um argumento é passado de tal forma que o procedimento chamado ou a propriedade não pode alterar o valor de uma variável subjacente ao argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="998d3-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="998d3-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="998d3-104">Remarks</span></span>  
 <span data-ttu-id="998d3-105">O `ByVal` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="998d3-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="998d3-106">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="998d3-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="998d3-107">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="998d3-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="998d3-108">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="998d3-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="998d3-109">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="998d3-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="998d3-110">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="998d3-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="998d3-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="998d3-111">Example</span></span>  
 <span data-ttu-id="998d3-112">O exemplo a seguir demonstra o uso do `ByVal` mecanismo com um argumento de tipo de referência de passagem de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="998d3-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="998d3-113">No exemplo, o argumento é `c1`, uma instância da classe `Class1`.</span><span class="sxs-lookup"><span data-stu-id="998d3-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="998d3-114">`ByVal`impede que o código nos procedimentos de alterar o valor subjacente do argumento de referência, `c1`, mas não protegerá os campos acessíveis e as propriedades de `c1`.</span><span class="sxs-lookup"><span data-stu-id="998d3-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 <span data-ttu-id="998d3-115">[!code-vb[VbVbalrKeywords n º&10;](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="998d3-115">[!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998d3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="998d3-116">See Also</span></span>  
 <span data-ttu-id="998d3-117">[Palavras-chave](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="998d3-117">[Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="998d3-118"> [Passando Argumentos por Valor e por Referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)</span><span class="sxs-lookup"><span data-stu-id="998d3-118"> [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)</span></span>
