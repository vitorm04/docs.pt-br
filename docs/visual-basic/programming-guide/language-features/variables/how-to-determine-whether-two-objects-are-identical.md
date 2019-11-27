---
title: Como determinar se dois objetos são idênticos
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348607"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="ae5dc-102">Como determinar se dois objetos são idênticos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae5dc-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="ae5dc-103">Em Visual Basic, duas referências de variáveis são consideradas idênticas se seus ponteiros forem iguais, ou seja, se ambas as variáveis apontarem para a mesma instância de classe na memória.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="ae5dc-104">Por exemplo, em um aplicativo Windows Forms, talvez você queira fazer uma comparação para determinar se a instância atual (`Me`) é igual a uma instância específica, como `Form2`.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="ae5dc-105">Visual Basic fornece dois operadores para comparar ponteiros.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="ae5dc-106">O [operador is](../../../../visual-basic/language-reference/operators/is-operator.md) retornará `True` se os objetos forem idênticos e o [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) retornar `True` se não forem.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="ae5dc-107">Determinando se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="ae5dc-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="ae5dc-108">Para determinar se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="ae5dc-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="ae5dc-109">Configure uma expressão de `Boolean` para testar os dois objetos.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="ae5dc-110">Em sua expressão de teste, use o operador `Is` com os dois objetos como operandos.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="ae5dc-111">`Is` retornará `True` se os objetos apontarem para a mesma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="ae5dc-112">Determinando se dois objetos não são idênticos</span><span class="sxs-lookup"><span data-stu-id="ae5dc-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="ae5dc-113">Às vezes, você deseja executar uma ação se os dois objetos não forem idênticos, e pode ser estranho combinar `Not` e `Is`, por exemplo `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="ae5dc-114">Nesse caso, você pode usar o operador de `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="ae5dc-115">Para determinar se dois objetos não são idênticos</span><span class="sxs-lookup"><span data-stu-id="ae5dc-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="ae5dc-116">Configure uma expressão de `Boolean` para testar os dois objetos.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="ae5dc-117">Em sua expressão de teste, use o operador `IsNot` com os dois objetos como operandos.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="ae5dc-118">`IsNot` retornará `True` se os objetos não apontarem para a mesma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae5dc-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae5dc-119">Example</span></span>  
 <span data-ttu-id="ae5dc-120">O exemplo a seguir testa pares de `Object` variáveis para ver se eles apontam para a mesma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="ae5dc-121">O exemplo anterior exibe a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="ae5dc-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="ae5dc-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae5dc-122">See also</span></span>

- [<span data-ttu-id="ae5dc-123">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="ae5dc-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="ae5dc-124">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="ae5dc-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="ae5dc-125">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="ae5dc-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="ae5dc-126">Operador Is</span><span class="sxs-lookup"><span data-stu-id="ae5dc-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="ae5dc-127">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="ae5dc-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="ae5dc-128">Como determinar se dois objetos estão relacionados</span><span class="sxs-lookup"><span data-stu-id="ae5dc-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="ae5dc-129">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="ae5dc-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
