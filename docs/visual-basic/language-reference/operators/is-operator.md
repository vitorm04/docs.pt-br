---
title: Operador is (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.is
dev_langs:
- VB
helpviewer_keywords:
- comparison operators
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: 12
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: b74d5c1a4574abe0b37acd62313be28823b5c8ce
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="35b4c-102">Operador Is (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35b4c-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="35b4c-103">Compara duas variáveis de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="35b4c-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35b4c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35b4c-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="35b4c-105">Partes</span><span class="sxs-lookup"><span data-stu-id="35b4c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="35b4c-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="35b4c-106">Required.</span></span> <span data-ttu-id="35b4c-107">Qualquer `Boolean` valor.</span><span class="sxs-lookup"><span data-stu-id="35b4c-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="35b4c-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="35b4c-108">Required.</span></span> <span data-ttu-id="35b4c-109">Qualquer `Object` nome.</span><span class="sxs-lookup"><span data-stu-id="35b4c-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="35b4c-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="35b4c-110">Required.</span></span> <span data-ttu-id="35b4c-111">Qualquer `Object` nome.</span><span class="sxs-lookup"><span data-stu-id="35b4c-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35b4c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="35b4c-112">Remarks</span></span>  
 <span data-ttu-id="35b4c-113">O `Is` operador determina se duas referências de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="35b4c-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="35b4c-114">No entanto, ele não realiza comparações de valor.</span><span class="sxs-lookup"><span data-stu-id="35b4c-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="35b4c-115">Se `object1` e `object2` se referir à mesma instância de objeto, `result` é `True`; se não, `result` é `False`.</span><span class="sxs-lookup"><span data-stu-id="35b4c-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="35b4c-116">`Is`também pode ser usado com o `TypeOf` palavra-chave para tornar um `TypeOf`... `Is` expressão, que testa se uma variável de objeto é compatível com um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="35b4c-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35b4c-117">O `Is` palavra-chave também é usada a [selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="35b4c-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35b4c-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35b4c-118">Example</span></span>  
 <span data-ttu-id="35b4c-119">O exemplo a seguir usa o `Is` operador para comparar pares de referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="35b4c-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="35b4c-120">Os resultados são atribuídos a um `Boolean` valor representando se os dois objetos são idênticos.</span><span class="sxs-lookup"><span data-stu-id="35b4c-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 <span data-ttu-id="35b4c-121">[!code-vb[VbVbalrOperators&#27;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="35b4c-121">[!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="35b4c-122">Conforme demonstrado no exemplo anterior, você pode usar o `Is` operador para o teste com associação antecipada e objetos com associação tardia.</span><span class="sxs-lookup"><span data-stu-id="35b4c-122">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b4c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35b4c-123">See Also</span></span>  
 <span data-ttu-id="35b4c-124">[Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="35b4c-124">[TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md) </span></span>  
<span data-ttu-id="35b4c-125"> [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="35b4c-125"> [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="35b4c-126"> [Operadores de comparação em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="35b4c-126"> [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="35b4c-127"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="35b4c-127"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="35b4c-128"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="35b4c-128"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="35b4c-129"> [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span><span class="sxs-lookup"><span data-stu-id="35b4c-129"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span></span>

