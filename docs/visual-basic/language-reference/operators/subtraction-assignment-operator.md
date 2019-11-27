---
title: Operador -=
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
ms.openlocfilehash: 44cb226d64e9f0b86c6566eb25fbafd6323a6d4c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347807"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="f571f-102">Operador -= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f571f-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="f571f-103">Subtrai o valor de uma expressão do valor de uma variável ou propriedade e atribui o resultado à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="f571f-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f571f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f571f-104">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f571f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="f571f-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="f571f-106">Necessária.</span><span class="sxs-lookup"><span data-stu-id="f571f-106">Required.</span></span> <span data-ttu-id="f571f-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="f571f-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="f571f-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="f571f-108">Required.</span></span> <span data-ttu-id="f571f-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="f571f-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f571f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f571f-110">Remarks</span></span>  
 <span data-ttu-id="f571f-111">O elemento no lado esquerdo do operador de `-=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="f571f-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f571f-112">A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="f571f-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="f571f-113">Primeiro, o operador de `-=` subtrai o valor da expressão (no lado direito do operador) do valor da variável ou da propriedade (no lado esquerdo do operador)...</span><span class="sxs-lookup"><span data-stu-id="f571f-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="f571f-114">Em seguida, o operador atribui o resultado dessa operação à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="f571f-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f571f-115">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="f571f-115">Overloading</span></span>  
 <span data-ttu-id="f571f-116">O [operador-(Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f571f-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f571f-117">Sobrecarregar o operador de `-` afeta o comportamento do operador `-=`.</span><span class="sxs-lookup"><span data-stu-id="f571f-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="f571f-118">Se o seu código usar `-=` em uma classe ou estrutura que sobrecarrega `-`, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="f571f-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f571f-119">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f571f-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f571f-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f571f-120">Example</span></span>  
 <span data-ttu-id="f571f-121">O exemplo a seguir usa o operador `-=` para subtrair uma variável `Integer` de outra e atribuir o resultado à última variável.</span><span class="sxs-lookup"><span data-stu-id="f571f-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="f571f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f571f-122">See also</span></span>

- [<span data-ttu-id="f571f-123">-Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f571f-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="f571f-124">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="f571f-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="f571f-125">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="f571f-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="f571f-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f571f-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f571f-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="f571f-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f571f-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="f571f-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
