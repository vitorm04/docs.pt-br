---
title: '&gt;&gt;= Operador (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7e388471b9adf424c55b1ad1042e5aed1ea8ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="affef-102">&gt;&gt;= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="affef-102">&gt;&gt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="affef-103">Executa um deslocamento aritmético para a direita no valor de uma variável ou propriedade e atribui o resultado de volta para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="affef-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="affef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="affef-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="affef-105">Partes</span><span class="sxs-lookup"><span data-stu-id="affef-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="affef-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="affef-106">Required.</span></span> <span data-ttu-id="affef-107">Variável ou propriedade de um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="affef-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="affef-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="affef-108">Required.</span></span> <span data-ttu-id="affef-109">Expressão numérica de um tipo de dados que amplia a `Integer`.</span><span class="sxs-lookup"><span data-stu-id="affef-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="affef-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="affef-110">Remarks</span></span>  
 <span data-ttu-id="affef-111">O elemento à esquerda do `>>=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="affef-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="affef-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="affef-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="affef-113">O `>>=` operador primeiro executa um deslocamento aritmético para a direita no valor da variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="affef-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="affef-114">O operador, em seguida, atribui o resultado da operação para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="affef-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="affef-115">Deslocamentos aritméticos não são circulares, que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="affef-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="affef-116">Em um deslocamento aritmético à direita, os bits deslocados além da posição de bit mais à direita são descartados e o bit mais à esquerda é propagado para as posições de bits vagas à esquerda.</span><span class="sxs-lookup"><span data-stu-id="affef-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="affef-117">Isso significa que se `variableorproperty` tem um valor negativo, as posições vazias são definidas como um.</span><span class="sxs-lookup"><span data-stu-id="affef-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="affef-118">Se `variableorproperty` for positivo, ou se seu tipo de dados é um tipo não assinado, as posições vazias são definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="affef-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="affef-119">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="affef-119">Overloading</span></span>  
 <span data-ttu-id="affef-120">O [>> operador](../../../visual-basic/language-reference/operators/right-shift-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="affef-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="affef-121">Sobrecarga de `>>` operador afeta o comportamento do `>>=` operador.</span><span class="sxs-lookup"><span data-stu-id="affef-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="affef-122">Se seu código usa `>>=` em uma classe ou estrutura que sobrecarrega `>>`, certifique-se de compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="affef-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="affef-123">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="affef-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="affef-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="affef-124">Example</span></span>  
 <span data-ttu-id="affef-125">O exemplo a seguir usa o `>>=` operador para deslocar o padrão de bits de um `Integer` variável diretamente pela quantidade especificada e atribui o resultado à variável.</span><span class="sxs-lookup"><span data-stu-id="affef-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="affef-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="affef-126">See Also</span></span>  
 [<span data-ttu-id="affef-127">Operador >></span><span class="sxs-lookup"><span data-stu-id="affef-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [<span data-ttu-id="affef-128">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="affef-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="affef-129">Operadores Bit Shift</span><span class="sxs-lookup"><span data-stu-id="affef-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="affef-130">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="affef-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="affef-131">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="affef-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="affef-132">Instruções</span><span class="sxs-lookup"><span data-stu-id="affef-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
