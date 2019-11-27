---
title: Operador Is
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349540"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="f55ff-102">Operador Is (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f55ff-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="f55ff-103">Compara duas variáveis de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="f55ff-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f55ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f55ff-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="f55ff-105">Partes</span><span class="sxs-lookup"><span data-stu-id="f55ff-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f55ff-106">Necessária.</span><span class="sxs-lookup"><span data-stu-id="f55ff-106">Required.</span></span> <span data-ttu-id="f55ff-107">Qualquer valor de `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="f55ff-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="f55ff-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="f55ff-108">Required.</span></span> <span data-ttu-id="f55ff-109">Qualquer `Object` nome.</span><span class="sxs-lookup"><span data-stu-id="f55ff-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="f55ff-110">Necessária.</span><span class="sxs-lookup"><span data-stu-id="f55ff-110">Required.</span></span> <span data-ttu-id="f55ff-111">Qualquer `Object` nome.</span><span class="sxs-lookup"><span data-stu-id="f55ff-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f55ff-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f55ff-112">Remarks</span></span>  
 <span data-ttu-id="f55ff-113">O operador `Is` determina se duas referências de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="f55ff-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="f55ff-114">No entanto, ele não executa comparações de valor.</span><span class="sxs-lookup"><span data-stu-id="f55ff-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="f55ff-115">Se `object1` e `object2` fizerem referência exatamente à mesma instância de objeto, `result` será `True`; Se não tiverem, `result` será `False`.</span><span class="sxs-lookup"><span data-stu-id="f55ff-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="f55ff-116">`Is` também pode ser usado com a palavra-chave `TypeOf` para criar uma expressão `TypeOf`...`Is`, que testa se uma variável de objeto é compatível com um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f55ff-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f55ff-117">A palavra-chave `Is` também é usada no [Select... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f55ff-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f55ff-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f55ff-118">Example</span></span>  
 <span data-ttu-id="f55ff-119">O exemplo a seguir usa o operador `Is` para comparar pares de referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="f55ff-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="f55ff-120">Os resultados são atribuídos a um valor `Boolean` que representa se os dois objetos são idênticos.</span><span class="sxs-lookup"><span data-stu-id="f55ff-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="f55ff-121">Como demonstra o exemplo anterior, você pode usar o operador `Is` para testar os objetos ligados antecipadamente e associação tardia.</span><span class="sxs-lookup"><span data-stu-id="f55ff-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f55ff-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f55ff-122">See also</span></span>

- [<span data-ttu-id="f55ff-123">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="f55ff-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="f55ff-124">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="f55ff-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="f55ff-125">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f55ff-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="f55ff-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f55ff-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f55ff-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="f55ff-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f55ff-128">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="f55ff-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
