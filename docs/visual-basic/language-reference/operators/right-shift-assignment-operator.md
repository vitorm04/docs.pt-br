---
title: '&gt;&gt;= Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>=
dev_langs:
- VB
helpviewer_keywords:
- assignment statements, compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 9cad053841c1e0c068cea44f8a5c8d4c84c50fcb
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="82ead-102">&gt;&gt;= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82ead-102">&gt;&gt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="82ead-103">Executa um deslocamento aritmético à direita no valor de uma variável ou propriedade e atribui o resultado de volta a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="82ead-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82ead-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82ead-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="82ead-105">Partes</span><span class="sxs-lookup"><span data-stu-id="82ead-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="82ead-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="82ead-106">Required.</span></span> <span data-ttu-id="82ead-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span><span class="sxs-lookup"><span data-stu-id="82ead-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="82ead-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="82ead-108">Required.</span></span> <span data-ttu-id="82ead-109">Expressão numérica de um tipo de dados que amplia a `Integer`.</span><span class="sxs-lookup"><span data-stu-id="82ead-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82ead-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="82ead-110">Remarks</span></span>  
 <span data-ttu-id="82ead-111">O elemento à esquerda do `>>=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="82ead-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="82ead-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="82ead-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="82ead-113">O `>>=` primeiro operador executa um deslocamento aritmético à direita no valor da variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="82ead-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="82ead-114">O operador atribui o resultado da operação para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="82ead-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="82ead-115">Deslocamentos aritméticos não são circulares, que significa que os bits deslocados de uma extremidade do resultado não são reconectados na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="82ead-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="82ead-116">Em um deslocamento aritmético à direita, os bits deslocados além da posição mais à direita de bits são descartados, e o bit mais à esquerda é propagado para as posições de bits vagas à esquerda.</span><span class="sxs-lookup"><span data-stu-id="82ead-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="82ead-117">Isso significa que se `variableorproperty` tem um valor negativo, as posições vagas são definidas como um.</span><span class="sxs-lookup"><span data-stu-id="82ead-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="82ead-118">Se `variableorproperty` for positivo, ou se seu tipo de dados é um tipo sem sinal, as posições vagas são definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="82ead-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="82ead-119">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="82ead-119">Overloading</span></span>  
 <span data-ttu-id="82ead-120">O [>> operador](../../../visual-basic/language-reference/operators/right-shift-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="82ead-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="82ead-121">Sobrecarga de `>>` operador afeta o comportamento do `>>=` operador.</span><span class="sxs-lookup"><span data-stu-id="82ead-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="82ead-122">Se seu código usa `>>=` em uma classe ou estrutura que sobrecarrega `>>`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="82ead-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="82ead-123">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="82ead-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82ead-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82ead-124">Example</span></span>  
 <span data-ttu-id="82ead-125">O exemplo a seguir usa o `>>=` operador para deslocar o padrão de bits de um `Integer` variável bem, a quantidade especificada e atribui o resultado à variável.</span><span class="sxs-lookup"><span data-stu-id="82ead-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 <span data-ttu-id="82ead-126">[!code-vb[VbVbalrOperators&#15;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="82ead-126">[!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ead-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82ead-127">See Also</span></span>  
 <span data-ttu-id="82ead-128">[>> Operador](../../../visual-basic/language-reference/operators/right-shift-operator.md) </span><span class="sxs-lookup"><span data-stu-id="82ead-128">[>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) </span></span>  
<span data-ttu-id="82ead-129"> [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="82ead-129"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="82ead-130"> [Operadores bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span><span class="sxs-lookup"><span data-stu-id="82ead-130"> [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span></span>  
<span data-ttu-id="82ead-131"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="82ead-131"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="82ead-132"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="82ead-132"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="82ead-133"> [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="82ead-133"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

