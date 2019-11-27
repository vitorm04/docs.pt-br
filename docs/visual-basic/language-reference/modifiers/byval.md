---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351593"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="6fa4d-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fa4d-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="6fa4d-103">Especifica que um argumento é passado [por valor](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de modo que o procedimento chamado ou a propriedade não possa alterar o valor de uma variável subjacente ao argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="6fa4d-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="6fa4d-104">Se nenhum modificador for especificado, ByVal será o padrão.</span><span class="sxs-lookup"><span data-stu-id="6fa4d-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="6fa4d-105">Como é o padrão, você não precisa especificar explicitamente a palavra-chave `ByVal` em assinaturas de método.</span><span class="sxs-lookup"><span data-stu-id="6fa4d-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="6fa4d-106">Ele tende a produzir código barulhento e, muitas vezes, leva à palavra-chave não padrão `ByRef` sendo ignorada.</span><span class="sxs-lookup"><span data-stu-id="6fa4d-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="6fa4d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fa4d-107">Remarks</span></span>
 <span data-ttu-id="6fa4d-108">O modificador de `ByVal` pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="6fa4d-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="6fa4d-109">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="6fa4d-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

 [<span data-ttu-id="6fa4d-110">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="6fa4d-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [<span data-ttu-id="6fa4d-111">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="6fa4d-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [<span data-ttu-id="6fa4d-112">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="6fa4d-112">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [<span data-ttu-id="6fa4d-113">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="6fa4d-113">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="6fa4d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fa4d-114">Example</span></span>
 <span data-ttu-id="6fa4d-115">O exemplo a seguir demonstra o uso do mecanismo de passagem de parâmetro `ByVal` com um argumento de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="6fa4d-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="6fa4d-116">No exemplo, o argumento é `c1`, uma instância da classe `Class1`.</span><span class="sxs-lookup"><span data-stu-id="6fa4d-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="6fa4d-117">`ByVal` impede que o código nos procedimentos altere o valor subjacente do argumento de referência, `c1`, mas não protege os campos e as propriedades acessíveis de `c1`.</span><span class="sxs-lookup"><span data-stu-id="6fa4d-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="6fa4d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fa4d-118">See also</span></span>

- [<span data-ttu-id="6fa4d-119">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="6fa4d-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="6fa4d-120">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="6fa4d-120">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
