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
ms.openlocfilehash: 5e534eac2300327d4c54c5ce93d8b2c6c538e794
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832484"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="73052-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73052-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="73052-103">Especifica que um argumento é passado de tal forma que o procedimento chamado ou a propriedade não é possível alterar o valor de uma variável subjacente ao argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="73052-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73052-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="73052-104">Remarks</span></span>  
 <span data-ttu-id="73052-105">O `ByVal` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="73052-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="73052-106">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="73052-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="73052-107">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="73052-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="73052-108">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="73052-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="73052-109">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="73052-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="73052-110">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="73052-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="73052-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73052-111">Example</span></span>  
 <span data-ttu-id="73052-112">O exemplo a seguir demonstra o uso do `ByVal` mecanismo com um argumento de tipo de referência de passagem de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="73052-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="73052-113">No exemplo, o argumento é `c1`, uma instância da classe `Class1`.</span><span class="sxs-lookup"><span data-stu-id="73052-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="73052-114">`ByVal` impede que o código nos procedimentos a alteração do valor subjacente do argumento de referência, `c1`, mas não protegerá acessíveis campos e propriedades de `c1`.</span><span class="sxs-lookup"><span data-stu-id="73052-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="73052-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73052-115">See also</span></span>

- [<span data-ttu-id="73052-116">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="73052-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="73052-117">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="73052-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
