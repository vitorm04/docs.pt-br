---
title: Operadores de concatenação no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: ab268e513e6f019ed651c94deb5e423cfcca7587
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="3706f-102">Operadores de concatenação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3706f-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="3706f-103">Os operadores de concatenação unem várias cadeias de caracteres em uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3706f-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="3706f-104">Existem dois operadores de concatenação, `+` e `&`.</span><span class="sxs-lookup"><span data-stu-id="3706f-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="3706f-105">Ambos realizam a operação de concatenação básica, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3706f-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="3706f-106">Esses operadores também podem concatenar variáveis `String`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3706f-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="3706f-107">Diferenças entre os dois operadores de concatenação</span><span class="sxs-lookup"><span data-stu-id="3706f-107">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="3706f-108">O [operador +](../../../../visual-basic/language-reference/operators/addition-operator.md) tem o objetivo principal de adição de dois números.</span><span class="sxs-lookup"><span data-stu-id="3706f-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="3706f-109">Entretanto, ele pode também concatenar operandos numéricos com operandos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3706f-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="3706f-110">O operador `+` possui um conjunto complexo de regras que determinam se adicionam, concatenam, sinalizam um erro do compilador ou emitem uma exceção <xref:System.InvalidCastException> de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3706f-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="3706f-111">O [& operador](../../../../visual-basic/language-reference/operators/concatenation-operator.md) é definida somente para `String` operandos e ele sempre será ampliada operandos para `String`, independentemente da configuração de `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="3706f-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="3706f-112">O operador `&` é recomendado para concatenação de cadeia de caracteres por ser definido exclusivamente para cadeias de caracteres e reduz suas chances de gerar uma conversão indesejada.</span><span class="sxs-lookup"><span data-stu-id="3706f-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="3706f-113">Desempenho: String e StringBuilder</span><span class="sxs-lookup"><span data-stu-id="3706f-113">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="3706f-114">Se você realizar um número significativo de manipulações em uma cadeia de caracteres, como concatenações, exclusões e substituições, seu desempenho poderá se beneficiar da classe <xref:System.Text.StringBuilder> no namespace <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="3706f-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="3706f-115">Ela usa uma instrução extra para criar e inicializar um objeto <xref:System.Text.StringBuilder> e outra instrução para converter seu valor final em uma `String`, mas você pode recuperar esse tempo, pois <xref:System.Text.StringBuilder> pode ser executado com mais rapidez.</span><span class="sxs-lookup"><span data-stu-id="3706f-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3706f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3706f-116">See Also</span></span>  
 [<span data-ttu-id="3706f-117">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="3706f-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="3706f-118">Tipos de métodos de manipulação de cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3706f-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [<span data-ttu-id="3706f-119">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3706f-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="3706f-120">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3706f-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="3706f-121">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3706f-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
