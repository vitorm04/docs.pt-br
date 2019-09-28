---
title: Operador /= (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: b4855e8270a329f9345339060a323b5ca9cd9792
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592184"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8709d-102">Operador /= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8709d-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="8709d-103">Divide o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado de ponto flutuante à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="8709d-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8709d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8709d-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="8709d-105">Partes</span><span class="sxs-lookup"><span data-stu-id="8709d-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8709d-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8709d-106">Required.</span></span> <span data-ttu-id="8709d-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="8709d-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="8709d-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8709d-108">Required.</span></span> <span data-ttu-id="8709d-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="8709d-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8709d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8709d-110">Remarks</span></span>  
 <span data-ttu-id="8709d-111">O elemento no lado esquerdo do operador `/=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="8709d-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8709d-112">A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8709d-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="8709d-113">Primeiro, o operador `/=` divide o valor da variável ou da propriedade (no lado esquerdo do operador) pelo valor da expressão (no lado direito do operador) de cada vez.</span><span class="sxs-lookup"><span data-stu-id="8709d-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="8709d-114">Em seguida, o operador atribui o resultado de ponto flutuante dessa operação à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="8709d-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="8709d-115">Essa instrução atribui um valor `Double` à variável ou à propriedade à esquerda.</span><span class="sxs-lookup"><span data-stu-id="8709d-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="8709d-116">Se `Option Strict` for `On`, `variableorproperty` deverá ser um `Double`.</span><span class="sxs-lookup"><span data-stu-id="8709d-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="8709d-117">Se `Option Strict` for `Off`, Visual Basic executará uma conversão implícita e atribuirá o valor resultante ao `variableorproperty`, com um possível erro no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8709d-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="8709d-118">Para obter mais informações, consulte [conversões de alargamento e estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8709d-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8709d-119">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="8709d-119">Overloading</span></span>  
 <span data-ttu-id="8709d-120">O [operador/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="8709d-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8709d-121">Sobrecarregar o operador `/` afeta o comportamento do operador `/=`.</span><span class="sxs-lookup"><span data-stu-id="8709d-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="8709d-122">Se seu código usar `/=` em uma classe ou estrutura que sobrecarrega `/`, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="8709d-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8709d-123">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8709d-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8709d-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8709d-124">Example</span></span>  
 <span data-ttu-id="8709d-125">O exemplo a seguir usa o operador `/=` para dividir uma variável `Integer` por um segundo e atribuir o quociente à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="8709d-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="8709d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8709d-126">See also</span></span>

- [<span data-ttu-id="8709d-127">Operador/(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8709d-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="8709d-128">Operador \\ =</span><span class="sxs-lookup"><span data-stu-id="8709d-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="8709d-129">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="8709d-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8709d-130">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="8709d-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="8709d-131">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8709d-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8709d-132">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="8709d-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8709d-133">Instruções</span><span class="sxs-lookup"><span data-stu-id="8709d-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
