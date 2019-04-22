---
title: Caracteres especiais no código (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 65fcd10521742e287c7934080b3352a06668df7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835551"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="65194-102">Caracteres especiais no código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65194-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="65194-103">Às vezes, você precisa usar caracteres especiais em seu código, ou seja, os caracteres que não estão em ordem alfabética ou numérica.</span><span class="sxs-lookup"><span data-stu-id="65194-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="65194-104">A pontuação e caracteres especiais no conjunto de caracteres do Visual Basic têm vários usos, desde a organização do texto do programa para definir as tarefas que o compilador ou o programa compilado executa.</span><span class="sxs-lookup"><span data-stu-id="65194-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="65194-105">Eles não especificam uma operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="65194-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="65194-106">Parênteses</span><span class="sxs-lookup"><span data-stu-id="65194-106">Parentheses</span></span>  
 <span data-ttu-id="65194-107">Use parênteses quando você define um procedimento, como um `Sub` ou `Function`.</span><span class="sxs-lookup"><span data-stu-id="65194-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="65194-108">Você deve colocar todas as listas de argumentos de procedimento entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="65194-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="65194-109">Você também usar parênteses para colocar as variáveis ou argumentos em grupos lógicos, especialmente para substituir a ordem padrão de precedência de operador em uma expressão complexa.</span><span class="sxs-lookup"><span data-stu-id="65194-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="65194-110">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="65194-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="65194-111">Após a execução do código anterior, o valor de `d` é 8.225 e o valor de `e` é 3.</span><span class="sxs-lookup"><span data-stu-id="65194-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="65194-112">O cálculo da `d` usa a prioridade padrão de `/` pela `+` e é equivalente a `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="65194-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="65194-113">Os parênteses no cálculo de `e` substituir a precedência padrão.</span><span class="sxs-lookup"><span data-stu-id="65194-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="65194-114">Separadores</span><span class="sxs-lookup"><span data-stu-id="65194-114">Separators</span></span>  
 <span data-ttu-id="65194-115">Separadores fazem o que seu nome sugere: separar seções de código.</span><span class="sxs-lookup"><span data-stu-id="65194-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="65194-116">No Visual Basic, o caractere separador é os dois-pontos (`:`).</span><span class="sxs-lookup"><span data-stu-id="65194-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="65194-117">Use separadores quando você deseja incluir várias instruções em uma única linha, em vez de linhas separadas.</span><span class="sxs-lookup"><span data-stu-id="65194-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="65194-118">Isso economiza espaço e melhora a legibilidade do código.</span><span class="sxs-lookup"><span data-stu-id="65194-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="65194-119">O exemplo a seguir mostra três instruções separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="65194-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="65194-120">Para obter mais informações, confira [Como: Quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="65194-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="65194-121">Os dois-pontos (`:`) caractere também é usado para identificar um rótulo de declaração.</span><span class="sxs-lookup"><span data-stu-id="65194-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="65194-122">Para obter mais informações, confira [Como: Rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="65194-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="65194-123">Concatenação</span><span class="sxs-lookup"><span data-stu-id="65194-123">Concatenation</span></span>  
 <span data-ttu-id="65194-124">Use o `&` operador para *concatenação*, ou vinculação de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="65194-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="65194-125">Não confunda isso com o `+` operador, que soma os valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="65194-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="65194-126">Se você usar o `+` operador para concatenar quando você opera em valores numéricos, você pode obter resultados incorretos.</span><span class="sxs-lookup"><span data-stu-id="65194-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="65194-127">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="65194-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="65194-128">Após a execução do código anterior, o valor de `resultA` é 21.01 e o valor de `resultB` é "10.0111".</span><span class="sxs-lookup"><span data-stu-id="65194-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="65194-129">Operadores de acesso de membro</span><span class="sxs-lookup"><span data-stu-id="65194-129">Member Access Operators</span></span>  
 <span data-ttu-id="65194-130">Para acessar um membro de um tipo, você pode usar o ponto (`.`) ou ponto de exclamação (`!`) operador entre o nome do tipo e o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="65194-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="65194-131">Ponto (.) Operador</span><span class="sxs-lookup"><span data-stu-id="65194-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="65194-132">Use o `.` operador em uma classe, estrutura, interface ou enumeração como um operador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="65194-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="65194-133">O membro pode ser um campo, propriedade, evento ou método.</span><span class="sxs-lookup"><span data-stu-id="65194-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="65194-134">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="65194-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="65194-135">Ponto de exclamação (!) Operador</span><span class="sxs-lookup"><span data-stu-id="65194-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="65194-136">Use o `!` operador apenas em uma classe ou interface como um operador de acesso do dicionário.</span><span class="sxs-lookup"><span data-stu-id="65194-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="65194-137">A classe ou interface deve ter uma propriedade padrão que aceita um único `String` argumento.</span><span class="sxs-lookup"><span data-stu-id="65194-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="65194-138">O identificador imediatamente após o `!` operador torna-se o valor do argumento passado para a propriedade padrão como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="65194-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="65194-139">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="65194-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="65194-140">As três linhas de saída `MsgBox` tudo exibir o valor `32856`.</span><span class="sxs-lookup"><span data-stu-id="65194-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="65194-141">A primeira linha usa o tradicional acesso à propriedade `index`, o segundo faz uso do fato de que `index` é a propriedade padrão da classe `hasDefault`, e o terceiro usa o acesso ao dicionário para a classe.</span><span class="sxs-lookup"><span data-stu-id="65194-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="65194-142">Observe que o segundo operando do `!` operador deve ser um identificador válido do Visual Basic não incluído entre aspas duplas (`" "`).</span><span class="sxs-lookup"><span data-stu-id="65194-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="65194-143">Em outras palavras, é possível usar um literal de cadeia de caracteres ou uma variável de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="65194-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="65194-144">A seguinte alteração para a última linha do `MsgBox` chamada gera um erro porque `"X"` é uma cadeia de caracteres literal.</span><span class="sxs-lookup"><span data-stu-id="65194-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="65194-145">Referências a coleções padrão devem ser explícitas.</span><span class="sxs-lookup"><span data-stu-id="65194-145">References to default collections must be explicit.</span></span> <span data-ttu-id="65194-146">Em particular, você não pode usar o `!` operador em uma variável de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="65194-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="65194-147">O `!` caractere também é usado como o `Single` caractere de tipo.</span><span class="sxs-lookup"><span data-stu-id="65194-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65194-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65194-148">See also</span></span>

- [<span data-ttu-id="65194-149">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="65194-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="65194-150">Caracteres de Tipo</span><span class="sxs-lookup"><span data-stu-id="65194-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
