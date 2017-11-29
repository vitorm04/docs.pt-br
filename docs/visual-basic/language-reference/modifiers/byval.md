---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c192cdb4ac43ad614fbfb663079c03ddc6c358c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="byval-visual-basic"></a><span data-ttu-id="1743a-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1743a-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="1743a-103">Especifica que um argumento é passado de tal forma que o procedimento chamado ou a propriedade não é possível alterar o valor de uma variável subjacente ao argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1743a-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1743a-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="1743a-104">Remarks</span></span>  
 <span data-ttu-id="1743a-105">O `ByVal` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="1743a-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1743a-106">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="1743a-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="1743a-107">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="1743a-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1743a-108">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="1743a-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="1743a-109">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="1743a-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1743a-110">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="1743a-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="1743a-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1743a-111">Example</span></span>  
 <span data-ttu-id="1743a-112">O exemplo a seguir demonstra o uso do `ByVal` mecanismo com um argumento de tipo de referência de passagem de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1743a-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="1743a-113">No exemplo, o argumento é `c1`, uma instância da classe `Class1`.</span><span class="sxs-lookup"><span data-stu-id="1743a-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="1743a-114">`ByVal`impede que o código nos procedimentos de alterar o valor subjacente do argumento de referência, `c1`, mas não protege acessíveis campos e propriedades de `c1`.</span><span class="sxs-lookup"><span data-stu-id="1743a-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1743a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1743a-115">See Also</span></span>  
 [<span data-ttu-id="1743a-116">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="1743a-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="1743a-117">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="1743a-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
