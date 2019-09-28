---
title: Operador ^= (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 382e0b27c2dbf27e5acccf29f1b8d2b002cb6664
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592229"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="65337-102">Operador ^= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65337-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="65337-103">Gera o valor de uma variável ou propriedade para a potência de uma expressão e atribui o resultado de volta à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="65337-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65337-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65337-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="65337-105">Partes</span><span class="sxs-lookup"><span data-stu-id="65337-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="65337-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="65337-106">Required.</span></span> <span data-ttu-id="65337-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="65337-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="65337-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="65337-108">Required.</span></span> <span data-ttu-id="65337-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="65337-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65337-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="65337-110">Remarks</span></span>  
 <span data-ttu-id="65337-111">O elemento no lado esquerdo do operador `^=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="65337-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="65337-112">A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="65337-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="65337-113">O operador `^=` primeiro gera o valor da variável ou da propriedade (no lado esquerdo do operador) com a potência do valor da expressão (no lado direito do operador)....</span><span class="sxs-lookup"><span data-stu-id="65337-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="65337-114">Em seguida, o operador atribui o resultado dessa operação de volta à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="65337-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="65337-115">Visual Basic sempre executa exponenciação no [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="65337-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="65337-116">Os operandos de qualquer tipo diferente são convertidos em `Double` e o resultado é sempre `Double`.</span><span class="sxs-lookup"><span data-stu-id="65337-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="65337-117">O valor de `expression` pode ser fracionário, negativo ou ambos.</span><span class="sxs-lookup"><span data-stu-id="65337-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="65337-118">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="65337-118">Overloading</span></span>  
 <span data-ttu-id="65337-119">O [operador ^](../../../visual-basic/language-reference/operators/exponentiation-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="65337-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="65337-120">Sobrecarregar o operador `^` afeta o comportamento do operador `^=`.</span><span class="sxs-lookup"><span data-stu-id="65337-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="65337-121">Se seu código usar `^=` em uma classe ou estrutura que sobrecarrega `^`, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="65337-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="65337-122">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="65337-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65337-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65337-123">Example</span></span>  
 <span data-ttu-id="65337-124">O exemplo a seguir usa o operador `^=` para aumentar o valor de uma variável `Integer` para a potência de uma segunda variável e atribuir o resultado à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="65337-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="65337-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65337-125">See also</span></span>

- [<span data-ttu-id="65337-126">Operador ^</span><span class="sxs-lookup"><span data-stu-id="65337-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [<span data-ttu-id="65337-127">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="65337-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="65337-128">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="65337-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="65337-129">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65337-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="65337-130">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="65337-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="65337-131">Instruções</span><span class="sxs-lookup"><span data-stu-id="65337-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
