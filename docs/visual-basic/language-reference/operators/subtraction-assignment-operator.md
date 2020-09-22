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
ms.openlocfilehash: 9149d9b350fc05c5e576f9f7800725aeb330e79d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873303"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="0d330-102">Operador -= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d330-102">-= Operator (Visual Basic)</span></span>

<span data-ttu-id="0d330-103">Subtrai o valor de uma expressão do valor de uma variável ou propriedade e atribui o resultado à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d330-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d330-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d330-104">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="0d330-105">Partes</span><span class="sxs-lookup"><span data-stu-id="0d330-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="0d330-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0d330-106">Required.</span></span> <span data-ttu-id="0d330-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d330-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="0d330-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="0d330-108">Required.</span></span> <span data-ttu-id="0d330-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="0d330-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d330-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d330-110">Remarks</span></span>  

 <span data-ttu-id="0d330-111">O elemento no lado esquerdo do `-=` operador pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="0d330-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="0d330-112">A variável ou a propriedade não pode ser [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="0d330-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="0d330-113">Primeiro, o `-=` operador subtrai o valor da expressão (no lado direito do operador) a partir do valor da variável ou da propriedade (no lado esquerdo do operador) do.</span><span class="sxs-lookup"><span data-stu-id="0d330-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="0d330-114">Em seguida, o operador atribui o resultado dessa operação à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d330-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0d330-115">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="0d330-115">Overloading</span></span>  

 <span data-ttu-id="0d330-116">O [operador-(Visual Basic)](subtraction-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0d330-116">The [- Operator (Visual Basic)](subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0d330-117">Sobrecarregar o `-` operador afeta o comportamento do `-=` operador.</span><span class="sxs-lookup"><span data-stu-id="0d330-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="0d330-118">Se o seu código usa `-=` em uma classe ou estrutura que sobrecarrega, certifique-se de `-` entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="0d330-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0d330-119">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0d330-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d330-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d330-120">Example</span></span>  

 <span data-ttu-id="0d330-121">O exemplo a seguir usa o `-=` operador para subtrair uma `Integer` variável de outra e atribuir o resultado à última variável.</span><span class="sxs-lookup"><span data-stu-id="0d330-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="0d330-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d330-122">See also</span></span>

- [<span data-ttu-id="0d330-123">Operador - (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d330-123">- Operator (Visual Basic)</span></span>](subtraction-operator.md)
- [<span data-ttu-id="0d330-124">Operadores de atribuição</span><span class="sxs-lookup"><span data-stu-id="0d330-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="0d330-125">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="0d330-125">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="0d330-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d330-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0d330-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="0d330-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0d330-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="0d330-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
