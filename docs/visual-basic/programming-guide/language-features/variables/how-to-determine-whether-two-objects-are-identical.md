---
title: "Como: determinar se dois objetos são idênticos (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- testing, objects
- objects [Visual Basic], comparing
- object variables, determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
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
ms.openlocfilehash: c9621412eb1429ed07d8861114a67a67b6c1d58c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="2ad86-102">Como determinar se dois objetos são idênticos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ad86-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="2ad86-103">Em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], duas referências de variáveis são consideradas idênticas se seus ponteiros são os mesmos, ou seja, se as duas variáveis apontam para a mesma instância de classe na memória.</span><span class="sxs-lookup"><span data-stu-id="2ad86-103">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="2ad86-104">Por exemplo, em um aplicativo Windows Forms, convém fazer uma comparação para determinar se a instância atual (`Me`) é o mesmo que uma determinada instância, como `Form2`.</span><span class="sxs-lookup"><span data-stu-id="2ad86-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="2ad86-105">fornece dois operadores para comparar ponteiros.</span><span class="sxs-lookup"><span data-stu-id="2ad86-105"> provides two operators to compare pointers.</span></span> <span data-ttu-id="2ad86-106">O [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) retorna `True` se os objetos são idênticos e o [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) retorna `True` se não forem.</span><span class="sxs-lookup"><span data-stu-id="2ad86-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="2ad86-107">Determinando se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="2ad86-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="2ad86-108">Para determinar se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="2ad86-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="2ad86-109">Configurar um `Boolean` para testar os dois objetos.</span><span class="sxs-lookup"><span data-stu-id="2ad86-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="2ad86-110">Na sua expressão de teste, use o `Is` operador com os dois objetos como operandos.</span><span class="sxs-lookup"><span data-stu-id="2ad86-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="2ad86-111">`Is`Retorna `True` se os dois objetos apontam para a mesma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="2ad86-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="2ad86-112">Determinando se dois objetos não são idênticos</span><span class="sxs-lookup"><span data-stu-id="2ad86-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="2ad86-113">Às vezes você deseja realizar uma ação se dois objetos não são idênticos, e pode ser complicado combinar `Not` e `Is`, por exemplo `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="2ad86-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="2ad86-114">Nesse caso, você pode usar o `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="2ad86-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="2ad86-115">Para determinar se dois objetos não são idênticos</span><span class="sxs-lookup"><span data-stu-id="2ad86-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="2ad86-116">Configurar um `Boolean` para testar os dois objetos.</span><span class="sxs-lookup"><span data-stu-id="2ad86-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="2ad86-117">Na sua expressão de teste, use o `IsNot` operador com os dois objetos como operandos.</span><span class="sxs-lookup"><span data-stu-id="2ad86-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="2ad86-118">`IsNot`Retorna `True` se os objetos não apontam para a mesma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="2ad86-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ad86-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2ad86-119">Example</span></span>  
 <span data-ttu-id="2ad86-120">O exemplo a seguir testa pares de `Object` variáveis para ver se eles apontam para a mesma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="2ad86-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 <span data-ttu-id="2ad86-121">[!code-vb[VbVbalrKeywords&#14;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad86-121">[!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]</span></span>  
  
 <span data-ttu-id="2ad86-122">O exemplo anterior exibe a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="2ad86-122">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="2ad86-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ad86-123">See Also</span></span>  
 <span data-ttu-id="2ad86-124">[Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="2ad86-124">[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="2ad86-125"> [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="2ad86-125"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="2ad86-126"> [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="2ad86-126"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="2ad86-127"> [Operador is](../../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2ad86-127"> [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="2ad86-128"> [Operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2ad86-128"> [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="2ad86-129"> [Como: determinar se dois objetos estão relacionados](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span><span class="sxs-lookup"><span data-stu-id="2ad86-129"> [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span></span>  
<span data-ttu-id="2ad86-130"> [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="2ad86-130"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>
