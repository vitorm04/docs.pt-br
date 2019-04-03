---
title: Operador -= (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: be1ff4f10f6b30d8448d2441ee3ad2c1e2f80e2d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815895"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="df1f3-102">Operador -= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df1f3-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="df1f3-103">Subtrai o valor de uma expressão do valor de uma variável ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="df1f3-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df1f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df1f3-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="df1f3-105">Partes</span><span class="sxs-lookup"><span data-stu-id="df1f3-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="df1f3-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df1f3-106">Required.</span></span> <span data-ttu-id="df1f3-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="df1f3-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="df1f3-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df1f3-108">Required.</span></span> <span data-ttu-id="df1f3-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="df1f3-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df1f3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="df1f3-110">Remarks</span></span>  
 <span data-ttu-id="df1f3-111">O elemento no lado esquerdo do `-=` operador pode ser uma variável escalar simple, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="df1f3-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="df1f3-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="df1f3-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="df1f3-113">O `-=` pela primeira vez, o operador subtrai o valor da expressão (no lado direito do operador) do valor da variável ou propriedade (no lado esquerdo do operador).</span><span class="sxs-lookup"><span data-stu-id="df1f3-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="df1f3-114">O operador, em seguida, atribui o resultado da operação para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="df1f3-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="df1f3-115">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="df1f3-115">Overloading</span></span>  
 <span data-ttu-id="df1f3-116">O [-operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="df1f3-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="df1f3-117">Sobrecarregando o `-` operador afeta o comportamento do `-=` operador.</span><span class="sxs-lookup"><span data-stu-id="df1f3-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="df1f3-118">Se seu código usa `-=` em uma classe ou estrutura que sobrecarrega `-`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="df1f3-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="df1f3-119">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="df1f3-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df1f3-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df1f3-120">Example</span></span>  
 <span data-ttu-id="df1f3-121">O exemplo a seguir usa o `-=` operador para subtrair um `Integer` variável da outra e atribui o resultado à última variável.</span><span class="sxs-lookup"><span data-stu-id="df1f3-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="df1f3-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df1f3-122">See also</span></span>

- [<span data-ttu-id="df1f3-123">-Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df1f3-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="df1f3-124">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="df1f3-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="df1f3-125">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="df1f3-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="df1f3-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="df1f3-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="df1f3-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="df1f3-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="df1f3-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="df1f3-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
