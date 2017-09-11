---
title: '&lt;&lt;= Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<<=
dev_langs:
- VB
helpviewer_keywords:
- operator <<=
- assignment statements, compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
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
ms.openlocfilehash: 517a5d0ea901bfe6f863b9da015365725ad7db7a
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="52292-102">&lt;&lt;= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52292-102">&lt;&lt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="52292-103">Executa um deslocamento aritmético à esquerda no valor de uma variável ou propriedade e atribui o resultado de volta a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="52292-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52292-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52292-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="52292-105">Partes</span><span class="sxs-lookup"><span data-stu-id="52292-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="52292-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="52292-106">Required.</span></span> <span data-ttu-id="52292-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span><span class="sxs-lookup"><span data-stu-id="52292-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="52292-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="52292-108">Required.</span></span> <span data-ttu-id="52292-109">Expressão numérica de um tipo de dados que amplia a `Integer`.</span><span class="sxs-lookup"><span data-stu-id="52292-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52292-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="52292-110">Remarks</span></span>  
 <span data-ttu-id="52292-111">O elemento à esquerda do `<<=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="52292-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="52292-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="52292-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="52292-113">O `<<=` primeiro operador executa um deslocamento aritmético à esquerda no valor da variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="52292-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="52292-114">O operador atribui o resultado da operação para essa variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="52292-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="52292-115">Deslocamentos aritméticos não são circulares, que significa que os bits deslocados de uma extremidade do resultado não são reconectados na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="52292-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="52292-116">Em um deslocamento aritmético à esquerda, os bits deslocados fora do intervalo do tipo de dados de resultado são descartados e as posições de bits vagas à direita são definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="52292-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="52292-117">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="52292-117">Overloading</span></span>  
 <span data-ttu-id="52292-118">O [ <> ](../../../visual-basic/language-reference/operators/left-shift-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="52292-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="52292-119">Sobrecarga de `<<` operador afeta o comportamento do `<<=` operador.</span><span class="sxs-lookup"><span data-stu-id="52292-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="52292-120">Se seu código usa `<<=` em uma classe ou estrutura que sobrecarrega `<<`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="52292-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="52292-121">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="52292-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52292-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52292-122">Example</span></span>  
 <span data-ttu-id="52292-123">O exemplo a seguir usa o `<<=` operador para deslocar o padrão de bits de um `Integer` variável deixados pela quantidade especificada e atribui o resultado à variável.</span><span class="sxs-lookup"><span data-stu-id="52292-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 <span data-ttu-id="52292-124">[!code-vb[VbVbalrOperators&13;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="52292-124">[!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52292-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52292-125">See Also</span></span>  
 <span data-ttu-id="52292-126">[<>](../../../visual-basic/language-reference/operators/left-shift-operator.md) </span><span class="sxs-lookup"><span data-stu-id="52292-126">[<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) </span></span>  
<span data-ttu-id="52292-127"> [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="52292-127"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="52292-128"> [Operadores bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span><span class="sxs-lookup"><span data-stu-id="52292-128"> [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span></span>  
<span data-ttu-id="52292-129"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="52292-129"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="52292-130"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="52292-130"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="52292-131"> [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="52292-131"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

