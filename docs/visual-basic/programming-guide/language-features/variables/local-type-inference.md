---
title: "Inferência de tipo local (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- local type inference
- vb.TypeInfer
dev_langs:
- VB
helpviewer_keywords:
- Option Infer statement
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: 43
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
ms.openlocfilehash: af8de63eb00db917771600f0fca8f200ec451afe
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="2ad2e-102">Inferência de tipo local (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ad2e-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="2ad2e-103">O compilador do Visual Basic usa *inferência de tipo* para determinar os tipos de dados de variáveis locais declarados sem um `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="2ad2e-104">O compilador infere o tipo da variável do tipo da expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="2ad2e-105">Isso permite que você declare variáveis sem especificar explicitamente um tipo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="2ad2e-106">Como resultado, as declarações ambos `num1` e `num2` são fortemente tipadas como inteiros.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 <span data-ttu-id="2ad2e-107">[!code-vb[VbVbalrTypeInference n º&1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad2e-107">[!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ad2e-108">Se você não quiser `num2` no exemplo anterior para ser digitado como um `Integer`, você pode especificar outro tipo usando uma declaração como `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-108">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  
  
 <span data-ttu-id="2ad2e-109">Inferência de tipo local se aplica no nível de procedimento.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="2ad2e-110">Ele não pode ser usado para declarar variáveis no nível de módulo (dentro de uma classe, estrutura, módulo ou interface mas não dentro de um procedimento ou bloco).</span><span class="sxs-lookup"><span data-stu-id="2ad2e-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="2ad2e-111">Se `num2` no exemplo anterior foram um campo de uma classe em vez de uma variável local em um procedimento, a declaração causa um erro com `Option Strict` e deseja classificar `num2` como um `Object` com `Option Strict` off.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="2ad2e-112">Da mesma forma, a inferência de tipo local não é válido para variáveis do nível de procedimento declaradas como `Static`.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="2ad2e-113">Tipo de inferência vs. Associação tardia</span><span class="sxs-lookup"><span data-stu-id="2ad2e-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="2ad2e-114">Código que usa inferência lembra o código que depende de ligação tardia.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="2ad2e-115">No entanto, inferência de tipos altamente variável em vez de deixá-lo como `Object`.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="2ad2e-116">O compilador usa um inicializador de variável para determinar o tipo da variável em tempo de compilação para produzir código early bound.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="2ad2e-117">No exemplo anterior, `num2`, como `num1`, é digitado como um `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="2ad2e-118">O comportamento de variáveis early bound difere das variáveis de ligação tardia, para o qual o tipo é conhecido somente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="2ad2e-119">Sabendo o tipo de início permite que o compilador identificar problemas antes da execução, alocar memória com precisão e execute outras otimizações.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="2ad2e-120">Associação antecipada também permite que o ambiente de desenvolvimento integrado (IDE) para fornecer o IntelliSense ajuda sobre os membros de um objeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="2ad2e-121">Associação antecipada também é preferencial para o desempenho.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="2ad2e-122">Isso ocorre porque todos os dados armazenados em uma variável de associação tardia devem ser encapsulados como tipo `Object`, e acessar os membros do tipo em tempo de execução faz com que o programa mais lento.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2ad2e-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2ad2e-123">Examples</span></span>  
 <span data-ttu-id="2ad2e-124">Inferência de tipo ocorre quando uma variável local é declarada sem uma `As` cláusula e inicializado.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="2ad2e-125">O compilador usa o tipo do valor inicial atribuído como o tipo da variável.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="2ad2e-126">Por exemplo, cada uma das linhas de código a seguir declara uma variável do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 <span data-ttu-id="2ad2e-127">[!code-vb[VbVbalrTypeInference n º&2;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad2e-127">[!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]</span></span>  
  
 <span data-ttu-id="2ad2e-128">O código a seguir demonstra duas maneiras equivalentes de criar uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-128">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 <span data-ttu-id="2ad2e-129">[!code-vb[VbVbalrTypeInference n º&3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad2e-129">[!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]</span></span>  
  
 <span data-ttu-id="2ad2e-130">É conveniente usar inferência de tipo para determinar o tipo de uma variável de controle de loop.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-130">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="2ad2e-131">No código a seguir, o compilador infere que `number` é um `Integer` porque `someNumbers2` do exemplo anterior é uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-131">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 <span data-ttu-id="2ad2e-132">[!code-vb[VbVbalrTypeInference n º&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad2e-132">[!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]</span></span>  
  
 <span data-ttu-id="2ad2e-133">Inferência de tipo local pode ser usada em `Using` instruções para estabelecer o tipo do nome do recurso, como demonstra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-133">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 <span data-ttu-id="2ad2e-134">[!code-vb[VbVbalrTypeInference&#7;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad2e-134">[!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]</span></span>  
  
 <span data-ttu-id="2ad2e-135">O tipo de uma variável também pode ser inferido de valores de retorno de funções, como demonstra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-135">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="2ad2e-136">Ambos `pList1` e `pList2` são matrizes de processos como `Process.GetProcesses` retorna uma matriz de processos.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-136">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 <span data-ttu-id="2ad2e-137">[!code-vb[VbVbalrTypeInference n º&5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad2e-137">[!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]</span></span>  
  
## <a name="option-infer"></a><span data-ttu-id="2ad2e-138">Option Infer</span><span class="sxs-lookup"><span data-stu-id="2ad2e-138">Option Infer</span></span>  
 <span data-ttu-id="2ad2e-139">`Option Infer`permite que você especifique se a inferência de tipo local é permitida em um arquivo específico.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-139">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="2ad2e-140">Para permitir ou bloquear a opção, digite uma das seguintes instruções no início do arquivo.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-140">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="2ad2e-141">Se você não especificar um valor para `Option Infer` em seu código, o padrão do compilador é `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-141">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="2ad2e-142">Para projetos atualizados do [!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb_orcas_long_md.md)] ou anterior, o padrão do compilador é `Option Infer Off`.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-142">For projects upgraded from [!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb_orcas_long_md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="2ad2e-143">Se o valor definido para `Option Infer` em um arquivo entrar em conflito com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-143">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="2ad2e-144">Para obter mais informações, consulte [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) e [página de compilação, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2ad2e-144">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="2ad2e-145">Restrições</span><span class="sxs-lookup"><span data-stu-id="2ad2e-145">Restrictions</span></span>  
 <span data-ttu-id="2ad2e-146">Inferência de tipos pode ser usada apenas para variáveis locais não estático; ele não pode ser usado para determinar o tipo de classe campos, propriedades ou funções.</span><span class="sxs-lookup"><span data-stu-id="2ad2e-146">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad2e-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ad2e-147">See Also</span></span>  
 <span data-ttu-id="2ad2e-148">[Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="2ad2e-148">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="2ad2e-149"> [Associação antecipada e tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span><span class="sxs-lookup"><span data-stu-id="2ad2e-149"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span></span>  
<span data-ttu-id="2ad2e-150"> [Para cada um... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2ad2e-150"> [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="2ad2e-151"> [Para... Próxima instrução](../../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2ad2e-151"> [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="2ad2e-152"> [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2ad2e-152"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="2ad2e-153"> [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="2ad2e-153"> [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="2ad2e-154"> [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="2ad2e-154"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
