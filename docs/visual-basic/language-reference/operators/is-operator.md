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
ms.openlocfilehash: 3cc0ae5f04358fbe6b2aabc50498f39ca7225164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370798"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="7018e-102">Operador Is (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7018e-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="7018e-103">Compara duas variáveis de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="7018e-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7018e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7018e-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="7018e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="7018e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="7018e-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="7018e-106">Required.</span></span> <span data-ttu-id="7018e-107">Qualquer `Boolean` valor.</span><span class="sxs-lookup"><span data-stu-id="7018e-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="7018e-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="7018e-108">Required.</span></span> <span data-ttu-id="7018e-109">Qualquer `Object` nome.</span><span class="sxs-lookup"><span data-stu-id="7018e-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="7018e-110">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="7018e-110">Required.</span></span> <span data-ttu-id="7018e-111">Qualquer `Object` nome.</span><span class="sxs-lookup"><span data-stu-id="7018e-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7018e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="7018e-112">Remarks</span></span>  
 <span data-ttu-id="7018e-113">O `Is` operador determina se duas referências de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="7018e-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="7018e-114">No entanto, ele não executa comparações de valor.</span><span class="sxs-lookup"><span data-stu-id="7018e-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="7018e-115">Se `object1` e `object2` ambos se referirem exatamente à mesma instância de objeto, `result` será `True` ; se não forem, `result` será `False` .</span><span class="sxs-lookup"><span data-stu-id="7018e-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="7018e-116">`Is`também pode ser usado com a `TypeOf` palavra-chave para criar uma `TypeOf` expressão... `Is` , que testa se uma variável de objeto é compatível com um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="7018e-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7018e-117">A `Is` palavra-chave também é usada no [Select... Instrução Case](../statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7018e-117">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7018e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7018e-118">Example</span></span>  
 <span data-ttu-id="7018e-119">O exemplo a seguir usa o `Is` operador para comparar pares de referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="7018e-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="7018e-120">Os resultados são atribuídos a um `Boolean` valor que representa se os dois objetos são idênticos.</span><span class="sxs-lookup"><span data-stu-id="7018e-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="7018e-121">Como demonstra o exemplo anterior, você pode usar o `Is` operador para testar os objetos ligados antecipadamente e associação tardia.</span><span class="sxs-lookup"><span data-stu-id="7018e-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7018e-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7018e-122">See also</span></span>

- [<span data-ttu-id="7018e-123">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="7018e-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="7018e-124">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="7018e-124">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="7018e-125">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7018e-125">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="7018e-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7018e-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="7018e-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="7018e-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="7018e-128">Operadores e expressões</span><span class="sxs-lookup"><span data-stu-id="7018e-128">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
