---
title: 'Como: Determinar se dois objetos são idêntico (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 62d73b6c3d706d9990be7783f0f3461fc0783d9f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512964"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="0898e-102">Como: Determinar se dois objetos são idêntico (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0898e-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="0898e-103">No Visual Basic, duas referências de variável são consideradas idênticas se os ponteiros são os mesmos, ou seja, se as duas variáveis apontam para a mesma instância de classe na memória.</span><span class="sxs-lookup"><span data-stu-id="0898e-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="0898e-104">Por exemplo, em um aplicativo de formulários do Windows, talvez você queira fazer uma comparação para determinar se a instância atual (`Me`) é o mesmo que uma determinada instância, como `Form2`.</span><span class="sxs-lookup"><span data-stu-id="0898e-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="0898e-105">Visual Basic fornece dois operadores para comparar ponteiros.</span><span class="sxs-lookup"><span data-stu-id="0898e-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="0898e-106">O [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) retorna `True` se os objetos forem idênticos e o [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) retorna `True` se eles não forem.</span><span class="sxs-lookup"><span data-stu-id="0898e-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="0898e-107">Determinando se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="0898e-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="0898e-108">Para determinar se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="0898e-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="0898e-109">Configurar um `Boolean` expressão para testar os dois objetos.</span><span class="sxs-lookup"><span data-stu-id="0898e-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="0898e-110">Em sua expressão de teste, use o `Is` operador com os dois objetos como operandos.</span><span class="sxs-lookup"><span data-stu-id="0898e-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="0898e-111">`Is` Retorna `True` se os objetos apontam para a mesma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="0898e-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="0898e-112">Determinando se dois objetos não são idênticos</span><span class="sxs-lookup"><span data-stu-id="0898e-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="0898e-113">Às vezes você deseja executar uma ação se dois objetos não são idênticos, e pode ser complicado combinar `Not` e `Is`, por exemplo `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="0898e-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="0898e-114">Nesse caso, você pode usar o `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="0898e-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="0898e-115">Para determinar se dois objetos não são idênticos</span><span class="sxs-lookup"><span data-stu-id="0898e-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="0898e-116">Configurar um `Boolean` expressão para testar os dois objetos.</span><span class="sxs-lookup"><span data-stu-id="0898e-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="0898e-117">Em sua expressão de teste, use o `IsNot` operador com os dois objetos como operandos.</span><span class="sxs-lookup"><span data-stu-id="0898e-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="0898e-118">`IsNot` Retorna `True` se os objetos não apontam para a mesma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="0898e-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0898e-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0898e-119">Example</span></span>  
 <span data-ttu-id="0898e-120">O exemplo a seguir testa pares de `Object` variáveis para ver se eles apontam para a mesma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="0898e-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 <span data-ttu-id="0898e-121">O exemplo anterior exibe a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="0898e-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="0898e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0898e-122">See also</span></span>
- [<span data-ttu-id="0898e-123">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="0898e-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="0898e-124">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="0898e-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="0898e-125">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="0898e-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="0898e-126">Operador Is</span><span class="sxs-lookup"><span data-stu-id="0898e-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="0898e-127">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="0898e-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="0898e-128">Como: Determinar se dois objetos estão relacionados</span><span class="sxs-lookup"><span data-stu-id="0898e-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="0898e-129">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="0898e-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
