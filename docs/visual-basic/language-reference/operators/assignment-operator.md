---
title: Operador =
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: eccea0b43564a4980778c9d1a5b8f9a8c2a9207d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874823"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="11afa-102">Operador = (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11afa-102">= Operator (Visual Basic)</span></span>

<span data-ttu-id="11afa-103">Atribui um valor a uma variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="11afa-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11afa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11afa-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="11afa-105">Partes</span><span class="sxs-lookup"><span data-stu-id="11afa-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="11afa-106">Qualquer variável gravável ou qualquer propriedade.</span><span class="sxs-lookup"><span data-stu-id="11afa-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="11afa-107">Qualquer literal, constante ou expressão.</span><span class="sxs-lookup"><span data-stu-id="11afa-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11afa-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="11afa-108">Remarks</span></span>  

 <span data-ttu-id="11afa-109">O elemento no lado esquerdo do sinal de igual ( `=` ) pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="11afa-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="11afa-110">A variável ou a propriedade não pode ser [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="11afa-110">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="11afa-111">O `=` operador atribui o valor à sua direita à variável ou à propriedade à esquerda.</span><span class="sxs-lookup"><span data-stu-id="11afa-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11afa-112">O `=` operador também é usado como um operador de comparação.</span><span class="sxs-lookup"><span data-stu-id="11afa-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="11afa-113">Para obter detalhes, consulte [operadores de comparação](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="11afa-113">For details, see [Comparison Operators](comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="11afa-114">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="11afa-114">Overloading</span></span>  

 <span data-ttu-id="11afa-115">O `=` operador só pode ser sobrecarregado como um operador de comparação relacional, não como um operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="11afa-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="11afa-116">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="11afa-116">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="11afa-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11afa-117">Example</span></span>  

 <span data-ttu-id="11afa-118">O exemplo a seguir demonstra o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="11afa-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="11afa-119">O valor à direita é atribuído à variável à esquerda.</span><span class="sxs-lookup"><span data-stu-id="11afa-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="11afa-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="11afa-120">See also</span></span>

- [<span data-ttu-id="11afa-121"> Operador&=</span><span class="sxs-lookup"><span data-stu-id="11afa-121">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="11afa-122">Operador \* =</span><span class="sxs-lookup"><span data-stu-id="11afa-122">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="11afa-123">Operador + =</span><span class="sxs-lookup"><span data-stu-id="11afa-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="11afa-124">-= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11afa-124">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="11afa-125">Operador/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11afa-125">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="11afa-126">\\= Operador</span><span class="sxs-lookup"><span data-stu-id="11afa-126">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="11afa-127">Operador ^ =</span><span class="sxs-lookup"><span data-stu-id="11afa-127">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="11afa-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="11afa-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="11afa-129">Operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="11afa-129">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="11afa-130">ReadOnly (somente-leitura)</span><span class="sxs-lookup"><span data-stu-id="11afa-130">ReadOnly</span></span>](../modifiers/readonly.md)
- [<span data-ttu-id="11afa-131">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="11afa-131">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
