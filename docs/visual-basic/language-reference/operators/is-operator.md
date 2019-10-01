---
title: Operador Is (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 0351d224d9bf08a8f3ca74090de7b9c51c2c61bf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701360"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="08ba6-102">Operador Is (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08ba6-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="08ba6-103">Compara duas variáveis de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="08ba6-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08ba6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08ba6-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="08ba6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="08ba6-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="08ba6-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="08ba6-106">Required.</span></span> <span data-ttu-id="08ba6-107">Qualquer valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="08ba6-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="08ba6-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="08ba6-108">Required.</span></span> <span data-ttu-id="08ba6-109">Qualquer nome `Object`.</span><span class="sxs-lookup"><span data-stu-id="08ba6-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="08ba6-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="08ba6-110">Required.</span></span> <span data-ttu-id="08ba6-111">Qualquer nome `Object`.</span><span class="sxs-lookup"><span data-stu-id="08ba6-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08ba6-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="08ba6-112">Remarks</span></span>  
 <span data-ttu-id="08ba6-113">O operador `Is` determina se duas referências de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="08ba6-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="08ba6-114">No entanto, ele não executa comparações de valor.</span><span class="sxs-lookup"><span data-stu-id="08ba6-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="08ba6-115">Se `object1` e `object2` fizerem referência exatamente à mesma instância de objeto, `result` será `True`; Se não tiverem, `result` será `False`.</span><span class="sxs-lookup"><span data-stu-id="08ba6-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="08ba6-116">`Is` também pode ser usado com a palavra-chave `TypeOf` para criar uma expressão `TypeOf`... `Is`, que testa se uma variável de objeto é compatível com um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="08ba6-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08ba6-117">A palavra-chave `Is` também é usada no [Select... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="08ba6-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08ba6-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08ba6-118">Example</span></span>  
 <span data-ttu-id="08ba6-119">O exemplo a seguir usa o operador `Is` para comparar pares de referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="08ba6-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="08ba6-120">Os resultados são atribuídos a um valor `Boolean` que representa se os dois objetos são idênticos.</span><span class="sxs-lookup"><span data-stu-id="08ba6-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="08ba6-121">Como demonstra o exemplo anterior, você pode usar o operador `Is` para testar os objetos ligados antecipadamente e associação tardia.</span><span class="sxs-lookup"><span data-stu-id="08ba6-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ba6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08ba6-122">See also</span></span>

- [<span data-ttu-id="08ba6-123">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="08ba6-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="08ba6-124">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="08ba6-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="08ba6-125">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08ba6-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="08ba6-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08ba6-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="08ba6-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="08ba6-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="08ba6-128">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="08ba6-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
