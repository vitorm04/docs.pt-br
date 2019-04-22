---
title: Operador TypeOf (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 7162fcc24595bbb16d268d5d9e1ea4d82f6e67fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829857"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="10f83-102">Operador TypeOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10f83-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="10f83-103">Compara uma variável de referência de objeto para um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="10f83-103">Compares an object reference variable to a data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f83-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10f83-104">Syntax</span></span>  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="10f83-105">Partes</span><span class="sxs-lookup"><span data-stu-id="10f83-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="10f83-106">Retornado.</span><span class="sxs-lookup"><span data-stu-id="10f83-106">Returned.</span></span> <span data-ttu-id="10f83-107">Um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="10f83-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="10f83-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="10f83-108">Required.</span></span> <span data-ttu-id="10f83-109">Qualquer expressão que é avaliada como um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="10f83-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="10f83-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="10f83-110">Required.</span></span> <span data-ttu-id="10f83-111">Qualquer tipo de dados nome.</span><span class="sxs-lookup"><span data-stu-id="10f83-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10f83-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="10f83-112">Remarks</span></span>  
 <span data-ttu-id="10f83-113">O `TypeOf` operador determina se o tempo de execução de tipo de `objectexpression` é compatível com `typename`.</span><span class="sxs-lookup"><span data-stu-id="10f83-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="10f83-114">A compatibilidade depende da categoria de tipo de `typename`.</span><span class="sxs-lookup"><span data-stu-id="10f83-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="10f83-115">A tabela a seguir mostra como a compatibilidade é determinada.</span><span class="sxs-lookup"><span data-stu-id="10f83-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="10f83-116">Categoria de tipo de `typename`</span><span class="sxs-lookup"><span data-stu-id="10f83-116">Type category of `typename`</span></span>|<span data-ttu-id="10f83-117">Critério de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="10f83-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="10f83-118">Classe</span><span class="sxs-lookup"><span data-stu-id="10f83-118">Class</span></span>|<span data-ttu-id="10f83-119">`objectexpression` é do tipo `typename` ou herda de `typename`</span><span class="sxs-lookup"><span data-stu-id="10f83-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="10f83-120">Estrutura</span><span class="sxs-lookup"><span data-stu-id="10f83-120">Structure</span></span>|<span data-ttu-id="10f83-121">`objectexpression` é do tipo `typename`</span><span class="sxs-lookup"><span data-stu-id="10f83-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="10f83-122">Interface</span><span class="sxs-lookup"><span data-stu-id="10f83-122">Interface</span></span>|<span data-ttu-id="10f83-123">`objectexpression` implementa `typename` ou herda de uma classe que implementa `typename`</span><span class="sxs-lookup"><span data-stu-id="10f83-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="10f83-124">Se o tipo de tempo de execução de `objectexpression` satisfaz o critério de compatibilidade `result` é `True`.</span><span class="sxs-lookup"><span data-stu-id="10f83-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="10f83-125">Caso contrário, `result` é `False`.</span><span class="sxs-lookup"><span data-stu-id="10f83-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="10f83-126">Se `objectexpression` for nulo, em seguida, `TypeOf`... `Is` retorna `False`, e... `IsNot` retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="10f83-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="10f83-127">`TypeOf` sempre é usado com o `Is` palavra-chave para construir um `TypeOf`... `Is` expressão, ou com o `IsNot` palavra-chave para construir um `TypeOf`... `IsNot` expressão.</span><span class="sxs-lookup"><span data-stu-id="10f83-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10f83-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10f83-128">Example</span></span>  
 <span data-ttu-id="10f83-129">O exemplo a seguir usa `TypeOf`... `Is` expressões para testar a compatibilidade das duas variáveis de referência com vários tipos de dados do objeto.</span><span class="sxs-lookup"><span data-stu-id="10f83-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="10f83-130">A variável `refInteger` tem um tipo de tempo de execução de `Integer`.</span><span class="sxs-lookup"><span data-stu-id="10f83-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="10f83-131">Ele é compatível com `Integer` , mas não com `Double`.</span><span class="sxs-lookup"><span data-stu-id="10f83-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="10f83-132">A variável `refForm` tem um tipo de tempo de execução de <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="10f83-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="10f83-133">Ele é compatível com <xref:System.Windows.Forms.Form> porque esse é o seu tipo, com <xref:System.Windows.Forms.Control> porque <xref:System.Windows.Forms.Form> herda <xref:System.Windows.Forms.Control>e com <xref:System.ComponentModel.IComponent> porque <xref:System.Windows.Forms.Form> herda de <xref:System.ComponentModel.Component>, que implementa <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="10f83-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="10f83-134">No entanto, `refForm` não é compatível com <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="10f83-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f83-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10f83-135">See also</span></span>

- [<span data-ttu-id="10f83-136">Operador Is</span><span class="sxs-lookup"><span data-stu-id="10f83-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="10f83-137">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="10f83-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="10f83-138">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10f83-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="10f83-139">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10f83-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="10f83-140">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="10f83-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="10f83-141">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="10f83-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
