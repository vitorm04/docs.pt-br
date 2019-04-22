---
title: Inferência de tipo local (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: e6214938262b987a1bae4a9ca1d5c945f8b7fe6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826815"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="5d5ba-102">Inferência de tipo local (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d5ba-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="5d5ba-103">O compilador do Visual Basic usa *inferência* para determinar os tipos de dados de variáveis locais declaradas sem um `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="5d5ba-104">O compilador infere o tipo da variável do tipo da expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="5d5ba-105">Isso permite que você declare variáveis sem especificar explicitamente um tipo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="5d5ba-106">Como resultado das declarações, ambos `num1` e `num2` são fortemente tipadas como inteiros.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  <span data-ttu-id="5d5ba-107">Se você não quiser `num2` no exemplo anterior para ser digitado como um `Integer`, você pode especificar outro tipo, usando uma declaração como `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="5d5ba-108">Inferência de tipo pode ser usada somente para as variáveis locais não-estático; ele não pode ser usado para determinar o tipo de funções, propriedades ou campos de classe.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="5d5ba-109">Inferência de tipo local se aplica no nível de procedimento.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="5d5ba-110">Ele não pode ser usado para declarar variáveis no nível de módulo (dentro de uma classe, estrutura, módulo ou interface mas não dentro de um procedimento ou bloco).</span><span class="sxs-lookup"><span data-stu-id="5d5ba-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="5d5ba-111">Se `num2` no exemplo anterior, foram um campo de uma classe em vez de uma variável local em um procedimento, a declaração poderia causar um erro com `Option Strict` e deseja classificar `num2` como um `Object` com `Option Strict` off.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="5d5ba-112">Da mesma forma, inferência de tipo local não se aplica a variáveis de nível de procedimento declaradas como `Static`.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="5d5ba-113">Vs de inferência de tipo. Associação tardia</span><span class="sxs-lookup"><span data-stu-id="5d5ba-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="5d5ba-114">Código que usa a inferência de tipo é semelhante ao código que dependa da ligação tardia.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="5d5ba-115">No entanto, inferência de tipos fortemente a variável em vez de deixá-lo como `Object`.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="5d5ba-116">O compilador usa o inicializador da variável para determinar o tipo da variável no tempo de compilação para produzir código early bound.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="5d5ba-117">No exemplo anterior, `num2`, como `num1`, é digitado como um `Integer`.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="5d5ba-118">O comportamento de variáveis de early bound difere das variáveis de associação tardia, para o qual o tipo é conhecido somente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="5d5ba-119">Saber o tipo no início, permite que o compilador identificar problemas antes da execução, alocar memória com precisão e execute outras otimizações.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="5d5ba-120">Associação antecipada também permite que o ambiente de desenvolvimento integrado (IDE) para fornecer o IntelliSense ajuda sobre os membros de um objeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="5d5ba-121">Associação antecipada também é preferencial para o desempenho.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="5d5ba-122">Isso ocorre porque todos os dados armazenados em uma variável de associação tardia devem ser encapsulados como tipo `Object`, e acesso a membros do tipo em tempo de execução faz com que o programa mais lento.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5d5ba-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5d5ba-123">Examples</span></span>  
 <span data-ttu-id="5d5ba-124">Inferência de tipo ocorre quando uma variável local é declarada sem uma `As` cláusula e inicializado.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="5d5ba-125">O compilador usa o tipo de valor inicial atribuído como o tipo da variável.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="5d5ba-126">Por exemplo, cada uma das seguintes linhas de código declara uma variável do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 <span data-ttu-id="5d5ba-127">O código a seguir demonstra duas maneiras equivalentes de criar uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 <span data-ttu-id="5d5ba-128">É conveniente usar inferência de tipo para determinar o tipo de uma variável de controle de loop.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="5d5ba-129">No código a seguir, o compilador infere que `number` é um `Integer` porque `someNumbers2` do exemplo anterior é uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 <span data-ttu-id="5d5ba-130">Inferência de tipo local pode ser usada em `Using` instruções para estabelecer o tipo do nome do recurso, como demonstra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 <span data-ttu-id="5d5ba-131">O tipo de uma variável também pode ser inferido de valores de retorno de funções, como o exemplo a seguir demonstra.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="5d5ba-132">Ambos `pList1` e `pList2` são matrizes de processos porque `Process.GetProcesses` retorna uma matriz de processos.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a><span data-ttu-id="5d5ba-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="5d5ba-133">Option Infer</span></span>  
 <span data-ttu-id="5d5ba-134">`Option Infer` permite que você especifique se a inferência de tipo local é permitida em um arquivo específico.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="5d5ba-135">Para habilitar ou bloquear a opção, digite uma das seguintes instruções no início do arquivo.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="5d5ba-136">Se você não especificar um valor para `Option Infer` em seu código, é o padrão do compilador `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="5d5ba-137">Para projetos atualizados do [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] ou versões anteriores, é o padrão do compilador `Option Infer Off`.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-137">For projects upgraded from [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="5d5ba-138">Se o valor definido para `Option Infer` em um arquivo entrar em conflito com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="5d5ba-139">Para obter mais informações, consulte [instrução opção inferir](../../../../visual-basic/language-reference/statements/option-infer-statement.md) e [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5d5ba-139">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5ba-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d5ba-140">See also</span></span>

- [<span data-ttu-id="5d5ba-141">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="5d5ba-141">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="5d5ba-142">Associação Antecipada e Tardia</span><span class="sxs-lookup"><span data-stu-id="5d5ba-142">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="5d5ba-143">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="5d5ba-143">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="5d5ba-144">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="5d5ba-144">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="5d5ba-145">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="5d5ba-145">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="5d5ba-146">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="5d5ba-146">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="5d5ba-147">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d5ba-147">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
