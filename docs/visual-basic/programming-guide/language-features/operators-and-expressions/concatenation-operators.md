---
title: "Operadores de concatenação no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators, Visual Basic strings
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: 18
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f255e168b9eb794ef846e0cc18dbbdba5941bec5
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="42715-102">Operadores de concatenação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42715-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="42715-103">Os operadores de concatenação unem várias cadeias de caracteres em uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="42715-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="42715-104">Existem dois operadores de concatenação, `+` e `&`.</span><span class="sxs-lookup"><span data-stu-id="42715-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="42715-105">Ambos realizam a operação de concatenação básica, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="42715-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="42715-106">Esses operadores também podem concatenar variáveis `String`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="42715-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 <span data-ttu-id="42715-107">[!code-vb[VbVbalrOperators&#76;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="42715-107">[!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]</span></span>  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="42715-108">Diferenças entre os dois operadores de concatenação</span><span class="sxs-lookup"><span data-stu-id="42715-108">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="42715-109">O [operador +](../../../../visual-basic/language-reference/operators/addition-operator.md) tem o objetivo principal de adicionar dois números.</span><span class="sxs-lookup"><span data-stu-id="42715-109">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="42715-110">Entretanto, ele pode também concatenar operandos numéricos com operandos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="42715-110">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="42715-111">O `+` operador tem um conjunto complexo de regras que determinam se adicionar, concatenar, sinalizar um erro do compilador ou lançar um tempo de execução <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="42715-111">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="42715-112">O [< / operador](../../../../visual-basic/language-reference/operators/concatenation-operator.md) é definido somente para `String` operandos e ele sempre amplia seus operandos para `String`, independentemente da configuração da `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="42715-112">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="42715-113">O operador `&` é recomendado para concatenação de cadeia de caracteres por ser definido exclusivamente para cadeias de caracteres e reduz suas chances de gerar uma conversão indesejada.</span><span class="sxs-lookup"><span data-stu-id="42715-113">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="42715-114">Desempenho: String e StringBuilder</span><span class="sxs-lookup"><span data-stu-id="42715-114">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="42715-115">Se você fizer um número significativo de manipulações em uma cadeia de caracteres, como concatenações, exclusões e substituições, seu desempenho poderá se beneficiar de <xref:System.Text.StringBuilder>classe o <xref:System.Text>namespace.</xref:System.Text> </xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="42715-115">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="42715-116">Ele usa uma instrução extra para criar e inicializar um <xref:System.Text.StringBuilder>objeto e outra instrução para converter o valor final para um `String`, mas você pode recuperar esse tempo porque <xref:System.Text.StringBuilder>pode ser executado mais rapidamente.</xref:System.Text.StringBuilder> </xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="42715-116">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42715-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42715-117">See Also</span></span>  
 <span data-ttu-id="42715-118">[Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="42715-118">[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="42715-119"> [Tipos de métodos de manipulação de cadeia de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md) </span><span class="sxs-lookup"><span data-stu-id="42715-119"> [Types of String Manipulation Methods in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md) </span></span>  
<span data-ttu-id="42715-120"> [Operadores aritméticos em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="42715-120"> [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="42715-121"> [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="42715-121"> [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="42715-122"> [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="42715-122"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>
