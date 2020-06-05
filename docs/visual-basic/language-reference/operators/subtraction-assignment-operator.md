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
ms.openlocfilehash: 4f403cd8a28f8d9d0ba1d24b0792a352a9c961db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406399"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="26e13-102">Operador -= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26e13-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="26e13-103">Subtrai o valor de uma expressão do valor de uma variável ou propriedade e atribui o resultado à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="26e13-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26e13-104">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="26e13-105">Partes</span><span class="sxs-lookup"><span data-stu-id="26e13-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="26e13-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="26e13-106">Required.</span></span> <span data-ttu-id="26e13-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="26e13-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="26e13-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="26e13-108">Required.</span></span> <span data-ttu-id="26e13-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="26e13-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26e13-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="26e13-110">Remarks</span></span>  
 <span data-ttu-id="26e13-111">O elemento no lado esquerdo do `-=` operador pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="26e13-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="26e13-112">A variável ou a propriedade não pode ser [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="26e13-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="26e13-113">Primeiro, o `-=` operador subtrai o valor da expressão (no lado direito do operador) a partir do valor da variável ou da propriedade (no lado esquerdo do operador) do.</span><span class="sxs-lookup"><span data-stu-id="26e13-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="26e13-114">Em seguida, o operador atribui o resultado dessa operação à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="26e13-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="26e13-115">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="26e13-115">Overloading</span></span>  
 <span data-ttu-id="26e13-116">O [operador-(Visual Basic)](subtraction-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="26e13-116">The [- Operator (Visual Basic)](subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="26e13-117">Sobrecarregar o `-` operador afeta o comportamento do `-=` operador.</span><span class="sxs-lookup"><span data-stu-id="26e13-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="26e13-118">Se o seu código usa `-=` em uma classe ou estrutura que sobrecarrega, certifique-se de `-` entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="26e13-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="26e13-119">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="26e13-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26e13-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26e13-120">Example</span></span>  
 <span data-ttu-id="26e13-121">O exemplo a seguir usa o `-=` operador para subtrair uma `Integer` variável de outra e atribuir o resultado à última variável.</span><span class="sxs-lookup"><span data-stu-id="26e13-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="26e13-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="26e13-122">See also</span></span>

- [<span data-ttu-id="26e13-123">-Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26e13-123">- Operator (Visual Basic)</span></span>](subtraction-operator.md)
- [<span data-ttu-id="26e13-124">Operadores de atribuição</span><span class="sxs-lookup"><span data-stu-id="26e13-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="26e13-125">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="26e13-125">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="26e13-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26e13-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="26e13-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="26e13-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="26e13-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="26e13-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
