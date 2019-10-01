---
title: Operador *= (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 47d3239af6ff24501e6babc23c0db4103c477796
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701063"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c51a8-102">Operador \*= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c51a8-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="c51a8-103">Multiplica o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="c51a8-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c51a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c51a8-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c51a8-105">Partes</span><span class="sxs-lookup"><span data-stu-id="c51a8-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="c51a8-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c51a8-106">Required.</span></span> <span data-ttu-id="c51a8-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="c51a8-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="c51a8-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c51a8-108">Required.</span></span> <span data-ttu-id="c51a8-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="c51a8-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c51a8-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c51a8-110">Remarks</span></span>  
 <span data-ttu-id="c51a8-111">O elemento no lado esquerdo do operador `*=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="c51a8-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="c51a8-112">A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="c51a8-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="c51a8-113">O operador de `*=` primeiro multiplica o valor da expressão (no lado direito do operador) pelo valor da variável ou da propriedade (no lado esquerdo do operador) de cada uma.</span><span class="sxs-lookup"><span data-stu-id="c51a8-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="c51a8-114">Em seguida, o operador atribui o resultado dessa operação à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="c51a8-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c51a8-115">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="c51a8-115">Overloading</span></span>  
 <span data-ttu-id="c51a8-116">O [operador \*](../../../visual-basic/language-reference/operators/multiplication-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="c51a8-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c51a8-117">Sobrecarregar o operador `*` afeta o comportamento do operador `*=`.</span><span class="sxs-lookup"><span data-stu-id="c51a8-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="c51a8-118">Se seu código usar `*=` em uma classe ou estrutura que sobrecarrega `*`, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="c51a8-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c51a8-119">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c51a8-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c51a8-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c51a8-120">Example</span></span>  
 <span data-ttu-id="c51a8-121">O exemplo a seguir usa o operador `*=` para multiplicar uma variável `Integer` por um segundo e atribuir o resultado à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="c51a8-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="c51a8-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c51a8-122">See also</span></span>

- [<span data-ttu-id="c51a8-123">Operador \*</span><span class="sxs-lookup"><span data-stu-id="c51a8-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="c51a8-124">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="c51a8-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="c51a8-125">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="c51a8-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="c51a8-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c51a8-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="c51a8-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c51a8-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="c51a8-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="c51a8-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
