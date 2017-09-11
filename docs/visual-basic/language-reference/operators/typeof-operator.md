---
title: Operador TypeOf (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- TypeOf
- vb.TypeOf
dev_langs:
- VB
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
caps.latest.revision: 11
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
ms.openlocfilehash: 677dcaaa8766b8ef89a0a9e0f1d9bbb27bd14281
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="2e062-102">Operador TypeOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e062-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="2e062-103">Compara uma variável de referência de objeto para um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="2e062-103">Compares an object reference variable to a data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e062-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e062-104">Syntax</span></span>  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="2e062-105">Partes</span><span class="sxs-lookup"><span data-stu-id="2e062-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="2e062-106">Retornado.</span><span class="sxs-lookup"><span data-stu-id="2e062-106">Returned.</span></span> <span data-ttu-id="2e062-107">Um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="2e062-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="2e062-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2e062-108">Required.</span></span> <span data-ttu-id="2e062-109">Qualquer expressão que é avaliada como um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="2e062-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="2e062-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2e062-110">Required.</span></span> <span data-ttu-id="2e062-111">Qualquer tipo de dados nome.</span><span class="sxs-lookup"><span data-stu-id="2e062-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e062-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e062-112">Remarks</span></span>  
 <span data-ttu-id="2e062-113">O `TypeOf` operador determina se o tempo de execução de tipo de `objectexpression` é compatível com `typename`.</span><span class="sxs-lookup"><span data-stu-id="2e062-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="2e062-114">A compatibilidade depende da categoria de tipo de `typename`.</span><span class="sxs-lookup"><span data-stu-id="2e062-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="2e062-115">A tabela a seguir mostra como compatibilidade é determinada.</span><span class="sxs-lookup"><span data-stu-id="2e062-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="2e062-116">Categoria de tipo de`typename`</span><span class="sxs-lookup"><span data-stu-id="2e062-116">Type category of `typename`</span></span>|<span data-ttu-id="2e062-117">Critério de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="2e062-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="2e062-118">Classe</span><span class="sxs-lookup"><span data-stu-id="2e062-118">Class</span></span>|<span data-ttu-id="2e062-119">`objectexpression`é do tipo `typename` ou herda de`typename`</span><span class="sxs-lookup"><span data-stu-id="2e062-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="2e062-120">Estrutura</span><span class="sxs-lookup"><span data-stu-id="2e062-120">Structure</span></span>|<span data-ttu-id="2e062-121">`objectexpression`é do tipo`typename`</span><span class="sxs-lookup"><span data-stu-id="2e062-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="2e062-122">Interface</span><span class="sxs-lookup"><span data-stu-id="2e062-122">Interface</span></span>|<span data-ttu-id="2e062-123">`objectexpression`implementa `typename` ou herda de uma classe que implementa`typename`</span><span class="sxs-lookup"><span data-stu-id="2e062-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="2e062-124">Se o tipo de tempo de execução do `objectexpression` satisfaz o critério de compatibilidade, `result` é `True`.</span><span class="sxs-lookup"><span data-stu-id="2e062-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="2e062-125">Caso contrário, `result` é `False`.</span><span class="sxs-lookup"><span data-stu-id="2e062-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="2e062-126">Se `objectexpression` for nulo, `TypeOf`... `Is` retorna `False`, e... `IsNot` returns `True`.</span><span class="sxs-lookup"><span data-stu-id="2e062-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="2e062-127">`TypeOf`é sempre usado com a `Is` palavra-chave para construir um `TypeOf`... `Is` expressão, ou com o `IsNot` palavra-chave para construir um `TypeOf`... `IsNot` expressão.</span><span class="sxs-lookup"><span data-stu-id="2e062-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e062-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e062-128">Example</span></span>  
 <span data-ttu-id="2e062-129">O exemplo a seguir usa `TypeOf`... `Is` para testar a compatibilidade das duas variáveis de referência com vários tipos de dados do objeto.</span><span class="sxs-lookup"><span data-stu-id="2e062-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 <span data-ttu-id="2e062-130">[!code-vb[VbVbalrOperators&#39;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2e062-130">[!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="2e062-131">A variável `refInteger` tem um tipo de tempo de execução de `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2e062-131">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="2e062-132">Ele é compatível com `Integer` , mas não com `Double`.</span><span class="sxs-lookup"><span data-stu-id="2e062-132">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="2e062-133">A variável `refForm` tem um tipo de tempo de execução de <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="2e062-133">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="2e062-134">Ele é compatível com <xref:System.Windows.Forms.Form>porque é seu tipo, com <xref:System.Windows.Forms.Control>porque <xref:System.Windows.Forms.Form>herda de <xref:System.Windows.Forms.Control>e com <xref:System.ComponentModel.IComponent>porque <xref:System.Windows.Forms.Form>herda de <xref:System.ComponentModel.Component>, que implementa o <xref:System.ComponentModel.IComponent>.</xref:System.ComponentModel.IComponent> </xref:System.ComponentModel.Component> </xref:System.Windows.Forms.Form> </xref:System.ComponentModel.IComponent> </xref:System.Windows.Forms.Control> </xref:System.Windows.Forms.Form> </xref:System.Windows.Forms.Control> </xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="2e062-134">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="2e062-135">No entanto, `refForm` não é compatível com <xref:System.Windows.Forms.Label>.</xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="2e062-135">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e062-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e062-136">See Also</span></span>  
 <span data-ttu-id="2e062-137">[Operador is](../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2e062-137">[Is Operator](../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="2e062-138"> [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="2e062-138"> [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="2e062-139"> [Operadores de comparação em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="2e062-139"> [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="2e062-140"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="2e062-140"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="2e062-141"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="2e062-141"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="2e062-142"> [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span><span class="sxs-lookup"><span data-stu-id="2e062-142"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span></span>

