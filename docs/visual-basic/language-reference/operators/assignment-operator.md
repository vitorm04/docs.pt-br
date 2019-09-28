---
title: Operador = (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: ca4c519dd80c07f54dc1c3dfe70daf6948446363
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591835"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8644b-102">Operador = (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8644b-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="8644b-103">Atribui um valor a uma variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="8644b-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8644b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8644b-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="8644b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="8644b-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8644b-106">Qualquer variável gravável ou qualquer propriedade.</span><span class="sxs-lookup"><span data-stu-id="8644b-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="8644b-107">Qualquer literal, constante ou expressão.</span><span class="sxs-lookup"><span data-stu-id="8644b-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8644b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8644b-108">Remarks</span></span>  
 <span data-ttu-id="8644b-109">O elemento no lado esquerdo do sinal de igual (`=`) pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="8644b-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8644b-110">A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8644b-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="8644b-111">O operador `=` atribui o valor à sua direita à variável ou à propriedade à esquerda.</span><span class="sxs-lookup"><span data-stu-id="8644b-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8644b-112">O operador `=` também é usado como um operador de comparação.</span><span class="sxs-lookup"><span data-stu-id="8644b-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="8644b-113">Para obter detalhes, consulte [operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8644b-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8644b-114">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="8644b-114">Overloading</span></span>  
 <span data-ttu-id="8644b-115">O operador `=` só pode ser sobrecarregado como um operador de comparação relacional, não como um operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="8644b-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="8644b-116">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8644b-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8644b-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8644b-117">Example</span></span>  
 <span data-ttu-id="8644b-118">O exemplo a seguir demonstra o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="8644b-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="8644b-119">O valor à direita é atribuído à variável à esquerda.</span><span class="sxs-lookup"><span data-stu-id="8644b-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="8644b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8644b-120">See also</span></span>

- [<span data-ttu-id="8644b-121">Operador &=</span><span class="sxs-lookup"><span data-stu-id="8644b-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="8644b-122">Operador \*=</span><span class="sxs-lookup"><span data-stu-id="8644b-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="8644b-123">Operador +=</span><span class="sxs-lookup"><span data-stu-id="8644b-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="8644b-124">-= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8644b-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="8644b-125">Operador/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8644b-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="8644b-126">Operador \\ =</span><span class="sxs-lookup"><span data-stu-id="8644b-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="8644b-127">Operador ^=</span><span class="sxs-lookup"><span data-stu-id="8644b-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="8644b-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="8644b-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="8644b-129">Operadores de Comparação</span><span class="sxs-lookup"><span data-stu-id="8644b-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="8644b-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="8644b-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="8644b-131">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="8644b-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
