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
ms.openlocfilehash: abfe1489cb7e0d06b03c308e0704ce6f69ee55da
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433809"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="aa6ff-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa6ff-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="aa6ff-103">Especifica que um argumento é passado [por valor](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de modo que o procedimento chamado ou a propriedade não possa alterar o valor de uma variável subjacente ao argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="aa6ff-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="aa6ff-104">Se nenhum modificador for especificado, ByVal será o padrão.</span><span class="sxs-lookup"><span data-stu-id="aa6ff-104">If no modifier is specified, ByVal is the default.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="aa6ff-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa6ff-105">Remarks</span></span>  
 <span data-ttu-id="aa6ff-106">O `ByVal` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="aa6ff-106">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="aa6ff-107">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="aa6ff-107">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="aa6ff-108">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="aa6ff-108">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="aa6ff-109">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="aa6ff-109">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="aa6ff-110">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="aa6ff-110">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="aa6ff-111">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="aa6ff-111">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="aa6ff-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa6ff-112">Example</span></span>  
 <span data-ttu-id="aa6ff-113">O exemplo a seguir demonstra o uso do `ByVal` mecanismo de passagem de parâmetro com um argumento de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="aa6ff-113">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="aa6ff-114">No exemplo, o argumento é `c1`uma instância da classe. `Class1`</span><span class="sxs-lookup"><span data-stu-id="aa6ff-114">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="aa6ff-115">`ByVal`impede que o código nos procedimentos altere o valor subjacente do argumento de referência, `c1`, mas não protege os campos e as propriedades acessíveis do. `c1`</span><span class="sxs-lookup"><span data-stu-id="aa6ff-115">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="aa6ff-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa6ff-116">See also</span></span>

- [<span data-ttu-id="aa6ff-117">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="aa6ff-117">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="aa6ff-118">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="aa6ff-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
