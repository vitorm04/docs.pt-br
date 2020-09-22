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
ms.openlocfilehash: 8daf6600f59cea343e0d02b99632b92ce4bf3183
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875476"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="687e2-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="687e2-102">ByVal (Visual Basic)</span></span>

<span data-ttu-id="687e2-103">Especifica que um argumento é passado [por valor](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de modo que o procedimento chamado ou a propriedade não possa alterar o valor de uma variável subjacente ao argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="687e2-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="687e2-104">Se nenhum modificador for especificado, ByVal será o padrão.</span><span class="sxs-lookup"><span data-stu-id="687e2-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="687e2-105">Como é o padrão, você não precisa especificar explicitamente a `ByVal` palavra-chave em assinaturas de método.</span><span class="sxs-lookup"><span data-stu-id="687e2-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="687e2-106">Ele tende a produzir código barulhento e, muitas vezes, leva à `ByRef` palavra-chave não-padrão que está sendo ignorada.</span><span class="sxs-lookup"><span data-stu-id="687e2-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="687e2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="687e2-107">Remarks</span></span>

 <span data-ttu-id="687e2-108">O `ByVal` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="687e2-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="687e2-109">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="687e2-109">Declare Statement</span></span>](../statements/declare-statement.md)

 [<span data-ttu-id="687e2-110">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="687e2-110">Function Statement</span></span>](../statements/function-statement.md)
  
 [<span data-ttu-id="687e2-111">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="687e2-111">Operator Statement</span></span>](../statements/operator-statement.md)
  
 [<span data-ttu-id="687e2-112">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="687e2-112">Property Statement</span></span>](../statements/property-statement.md)
  
 [<span data-ttu-id="687e2-113">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="687e2-113">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="687e2-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="687e2-114">Example</span></span>

 <span data-ttu-id="687e2-115">O exemplo a seguir demonstra o uso do `ByVal` mecanismo de passagem de parâmetro com um argumento de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="687e2-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="687e2-116">No exemplo, o argumento é `c1` uma instância da classe `Class1` .</span><span class="sxs-lookup"><span data-stu-id="687e2-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="687e2-117">`ByVal` impede que o código nos procedimentos altere o valor subjacente do argumento de referência, `c1` , mas não protege os campos e as propriedades acessíveis do `c1` .</span><span class="sxs-lookup"><span data-stu-id="687e2-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="687e2-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="687e2-118">See also</span></span>

- [<span data-ttu-id="687e2-119">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="687e2-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="687e2-120">Passar argumentos por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="687e2-120">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
