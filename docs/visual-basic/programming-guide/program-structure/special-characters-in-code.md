---
title: "Caracteres especiais no código (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
dev_langs:
- VB
helpviewer_keywords:
- special characters, in code
- parentheses, using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator
- concatenation operators, special characters in code
- concatenation operators, vs. addition operator
- '! operator'
- separators, using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator
- addition operator
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
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
ms.openlocfilehash: cd7fbce5c382c3acd88a12277a3d7899b823d049
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="b9a76-102">Caracteres especiais no código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9a76-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="b9a76-103">Às vezes, você precisa usar caracteres especiais em seu código, ou seja, caracteres não alfabéticos ou numéricos.</span><span class="sxs-lookup"><span data-stu-id="b9a76-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="b9a76-104">A pontuação e caracteres especiais na [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] conjunto de caracteres têm vários usos, desde a organização do texto do programa para definir as tarefas que o compilador ou o programa compilado executa.</span><span class="sxs-lookup"><span data-stu-id="b9a76-104">The punctuation and special characters in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="b9a76-105">Eles não especificam uma operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="b9a76-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="b9a76-106">Parênteses</span><span class="sxs-lookup"><span data-stu-id="b9a76-106">Parentheses</span></span>  
 <span data-ttu-id="b9a76-107">Use parênteses quando você define um procedimento, como um `Sub` ou `Function`.</span><span class="sxs-lookup"><span data-stu-id="b9a76-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="b9a76-108">Você deve colocar todas as listas de argumentos de procedimento entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="b9a76-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="b9a76-109">Você também usar parênteses para colocar as variáveis ou argumentos em grupos lógicos, especialmente para substituir a ordem padrão de precedência de operador em uma expressão complexa.</span><span class="sxs-lookup"><span data-stu-id="b9a76-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="b9a76-110">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="b9a76-110">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="b9a76-111">[!code-vb[VbVbcnConventions n º&11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b9a76-111">[!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]</span></span>  
  
 <span data-ttu-id="b9a76-112">Após a execução do código anterior, o valor de `d` é 8.225 e o valor de `e` é 3.</span><span class="sxs-lookup"><span data-stu-id="b9a76-112">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="b9a76-113">O cálculo de `d` usa a prioridade padrão de `/` pela `+` e é equivalente a `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="b9a76-113">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="b9a76-114">Os parênteses no cálculo de `e` substituem a precedência padrão.</span><span class="sxs-lookup"><span data-stu-id="b9a76-114">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="b9a76-115">Separadores</span><span class="sxs-lookup"><span data-stu-id="b9a76-115">Separators</span></span>  
 <span data-ttu-id="b9a76-116">Separadores fazem o que seu nome sugere: separar seções de código.</span><span class="sxs-lookup"><span data-stu-id="b9a76-116">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="b9a76-117">Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], o caractere separador é dois-pontos (`:`).</span><span class="sxs-lookup"><span data-stu-id="b9a76-117">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], the separator character is the colon (`:`).</span></span> <span data-ttu-id="b9a76-118">Use separadores quando você deseja incluir várias instruções em uma única linha, em vez de linhas separadas.</span><span class="sxs-lookup"><span data-stu-id="b9a76-118">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="b9a76-119">Isso economiza espaço e melhora a legibilidade do código.</span><span class="sxs-lookup"><span data-stu-id="b9a76-119">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="b9a76-120">O exemplo a seguir mostra três instruções separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="b9a76-120">The following example shows three statements separated by colons.</span></span>  
  
 <span data-ttu-id="b9a76-121">[!code-vb[VbVbcnConventions&#12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b9a76-121">[!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]</span></span>  
  
 <span data-ttu-id="b9a76-122">Para obter mais informações, consulte [como: Break e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="b9a76-122">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="b9a76-123">Os dois-pontos (`:`) caractere também é usado para identificar um rótulo de declaração.</span><span class="sxs-lookup"><span data-stu-id="b9a76-123">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="b9a76-124">Para obter mais informações, consulte [como: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="b9a76-124">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="b9a76-125">Concatenação</span><span class="sxs-lookup"><span data-stu-id="b9a76-125">Concatenation</span></span>  
 <span data-ttu-id="b9a76-126">Use o `&` operador para *concatenação*, ou vincular cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b9a76-126">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="b9a76-127">Não confunda isso com o `+` operador, que soma os valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="b9a76-127">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="b9a76-128">Se você usar o `+` operador para concatenar quando você opera em valores numéricos, você pode obter resultados incorretos.</span><span class="sxs-lookup"><span data-stu-id="b9a76-128">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="b9a76-129">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="b9a76-129">The following example demonstrates this.</span></span>  
  
 <span data-ttu-id="b9a76-130">[!code-vb[VbVbcnConventions&13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b9a76-130">[!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]</span></span>  
  
 <span data-ttu-id="b9a76-131">Após a execução do código anterior, o valor de `resultA` é 21.01 e o valor de `resultB` é "10.0111".</span><span class="sxs-lookup"><span data-stu-id="b9a76-131">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="b9a76-132">Operadores de acesso de membro</span><span class="sxs-lookup"><span data-stu-id="b9a76-132">Member Access Operators</span></span>  
 <span data-ttu-id="b9a76-133">Para acessar um membro de um tipo, você pode usar o ponto (`.`) ou ponto de exclamação (`!`) operador entre o nome do tipo e o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="b9a76-133">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="b9a76-134">Operador ponto (.) Operador</span><span class="sxs-lookup"><span data-stu-id="b9a76-134">Dot (.) Operator</span></span>  
 <span data-ttu-id="b9a76-135">Use o `.` operador em uma classe, estrutura, interface ou enumeração como um operador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="b9a76-135">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="b9a76-136">O membro pode ser um campo, propriedade, evento ou método.</span><span class="sxs-lookup"><span data-stu-id="b9a76-136">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="b9a76-137">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="b9a76-137">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="b9a76-138">[!code-vb[VbVbcnConventions&#14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b9a76-138">[!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]</span></span>  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="b9a76-139">Ponto de exclamação (!) Operador</span><span class="sxs-lookup"><span data-stu-id="b9a76-139">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="b9a76-140">Use o `!` operador apenas em uma classe ou interface como um operador de acesso de dicionário.</span><span class="sxs-lookup"><span data-stu-id="b9a76-140">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="b9a76-141">A classe ou interface deve ter uma propriedade padrão que aceita um único `String` argumento.</span><span class="sxs-lookup"><span data-stu-id="b9a76-141">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="b9a76-142">O identificador imediatamente após o `!` operador torna-se o valor do argumento passado para a propriedade padrão como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b9a76-142">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="b9a76-143">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="b9a76-143">The following example demonstrates this.</span></span>  
  
 <span data-ttu-id="b9a76-144">[!code-vb[VbVbcnConventions&#15;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="b9a76-144">[!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]</span></span>  
  
 <span data-ttu-id="b9a76-145">Saída de três linhas de `MsgBox` all Exibe o valor `32856`.</span><span class="sxs-lookup"><span data-stu-id="b9a76-145">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="b9a76-146">A primeira linha usa o acesso à propriedade tradicional `index`, o segundo faz uso do fato de que `index` é a propriedade padrão da classe `hasDefault`, e o terceiro usa dicionário acesso à classe.</span><span class="sxs-lookup"><span data-stu-id="b9a76-146">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="b9a76-147">Observe que o segundo operando do `!` operador deve ser um identificador válido Visual Basic não entre aspas duplas (`" "`).</span><span class="sxs-lookup"><span data-stu-id="b9a76-147">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="b9a76-148">Em outras palavras, você não pode usar uma cadeia de caracteres literal ou variável de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b9a76-148">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="b9a76-149">A seguinte alteração para a última linha do `MsgBox` chamada gera um erro porque `"X"` é uma de cadeia de caracteres literal.</span><span class="sxs-lookup"><span data-stu-id="b9a76-149">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="b9a76-150">Referências às coleções padrão devem ser explícitas.</span><span class="sxs-lookup"><span data-stu-id="b9a76-150">References to default collections must be explicit.</span></span> <span data-ttu-id="b9a76-151">Em particular, você não pode usar o `!` operador em uma variável de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="b9a76-151">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="b9a76-152">O `!` caractere também é usado como o `Single` caractere de tipo.</span><span class="sxs-lookup"><span data-stu-id="b9a76-152">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a76-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9a76-153">See Also</span></span>  
 <span data-ttu-id="b9a76-154">[Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="b9a76-154">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="b9a76-155"> [Caracteres de Tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span><span class="sxs-lookup"><span data-stu-id="b9a76-155"> [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span>
