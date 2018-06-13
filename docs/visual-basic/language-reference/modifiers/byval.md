---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 076289ff303dce58f036d6c7cb1505b151da19f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602977"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="ed46b-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed46b-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="ed46b-103">Especifica que um argumento é passado de tal forma que o procedimento chamado ou a propriedade não é possível alterar o valor de uma variável subjacente ao argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="ed46b-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed46b-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed46b-104">Remarks</span></span>  
 <span data-ttu-id="ed46b-105">O `ByVal` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="ed46b-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ed46b-106">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="ed46b-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="ed46b-107">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="ed46b-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ed46b-108">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="ed46b-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="ed46b-109">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="ed46b-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ed46b-110">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="ed46b-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="ed46b-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ed46b-111">Example</span></span>  
 <span data-ttu-id="ed46b-112">O exemplo a seguir demonstra o uso do `ByVal` mecanismo com um argumento de tipo de referência de passagem de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ed46b-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="ed46b-113">No exemplo, o argumento é `c1`, uma instância da classe `Class1`.</span><span class="sxs-lookup"><span data-stu-id="ed46b-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="ed46b-114">`ByVal` impede que o código nos procedimentos de alterar o valor subjacente do argumento de referência, `c1`, mas não protege acessíveis campos e propriedades de `c1`.</span><span class="sxs-lookup"><span data-stu-id="ed46b-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ed46b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed46b-115">See Also</span></span>  
 [<span data-ttu-id="ed46b-116">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ed46b-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="ed46b-117">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="ed46b-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
