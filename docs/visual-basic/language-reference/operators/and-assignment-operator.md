---
title: '&amp;= Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: dee30096f244adc34b83fdfdc6af0baabd372b4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672403"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="abb0e-102">&amp;= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abb0e-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="abb0e-103">Concatena uma `String` expressão para um `String` variável ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="abb0e-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abb0e-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="abb0e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="abb0e-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="abb0e-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="abb0e-106">Required.</span></span> <span data-ttu-id="abb0e-107">Qualquer `String` variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="abb0e-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="abb0e-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="abb0e-108">Required.</span></span> <span data-ttu-id="abb0e-109">Qualquer expressão de `String` .</span><span class="sxs-lookup"><span data-stu-id="abb0e-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abb0e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="abb0e-110">Remarks</span></span>  
 <span data-ttu-id="abb0e-111">O elemento no lado esquerdo do `&=` operador pode ser uma variável escalar simple, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="abb0e-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="abb0e-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="abb0e-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="abb0e-113">O `&=` operador concatena as `String` expressão à sua direita o `String` variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.</span><span class="sxs-lookup"><span data-stu-id="abb0e-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="abb0e-114">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="abb0e-114">Overloading</span></span>  
 <span data-ttu-id="abb0e-115">O [& operador](../../../visual-basic/language-reference/operators/concatenation-operator.md) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="abb0e-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="abb0e-116">Sobrecarregando o `&` operador afeta o comportamento do `&=` operador.</span><span class="sxs-lookup"><span data-stu-id="abb0e-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="abb0e-117">Se seu código usa `&=` em uma classe ou estrutura que sobrecarrega `&`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="abb0e-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="abb0e-118">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="abb0e-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="abb0e-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="abb0e-119">Example</span></span>  
 <span data-ttu-id="abb0e-120">O exemplo a seguir usa o `&=` operador para concatenar duas `String` variáveis e atribuir o resultado para a primeira variável.</span><span class="sxs-lookup"><span data-stu-id="abb0e-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="abb0e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abb0e-121">See also</span></span>
- [<span data-ttu-id="abb0e-122">Operador &</span><span class="sxs-lookup"><span data-stu-id="abb0e-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="abb0e-123">Operador +=</span><span class="sxs-lookup"><span data-stu-id="abb0e-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="abb0e-124">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="abb0e-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="abb0e-125">Operadores de Concatenação</span><span class="sxs-lookup"><span data-stu-id="abb0e-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="abb0e-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abb0e-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="abb0e-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="abb0e-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="abb0e-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="abb0e-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
