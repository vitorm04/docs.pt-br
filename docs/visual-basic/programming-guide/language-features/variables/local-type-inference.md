---
title: Inferência de tipo local
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
ms.openlocfilehash: 3979396d32aa5d3b853aa087d43f70d5987e510b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410393"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="0bb08-102">Inferência de tipo local (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bb08-102">Local Type Inference (Visual Basic)</span></span>

<span data-ttu-id="0bb08-103">O compilador de Visual Basic usa a *inferência de tipos* para determinar os tipos de dados de variáveis locais declarados sem uma `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="0bb08-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="0bb08-104">O compilador infere o tipo da variável do tipo da expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="0bb08-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="0bb08-105">Isso permite que você declare variáveis sem explicitamente indicar um tipo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0bb08-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="0bb08-106">Como resultado das declarações, ambos `num1` e `num2` são fortemente tipados como inteiros.</span><span class="sxs-lookup"><span data-stu-id="0bb08-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="0bb08-107">Se você não quiser que `num2` o exemplo anterior seja digitado como um `Integer` , você pode especificar outro tipo usando uma declaração como `Dim num3 As Object = 3` ou `Dim num4 As Double = 3` .</span><span class="sxs-lookup"><span data-stu-id="0bb08-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>

> [!NOTE]
> <span data-ttu-id="0bb08-108">A inferência de tipos pode ser usada somente para variáveis locais não estáticas; Ele não pode ser usado para determinar o tipo de campos de classe, propriedades ou funções.</span><span class="sxs-lookup"><span data-stu-id="0bb08-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>

<span data-ttu-id="0bb08-109">A inferência de tipo local se aplica ao nível de procedimento.</span><span class="sxs-lookup"><span data-stu-id="0bb08-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="0bb08-110">Ele não pode ser usado para declarar variáveis no nível do módulo (dentro de uma classe, estrutura, módulo ou interface, mas não dentro de um procedimento ou bloco).</span><span class="sxs-lookup"><span data-stu-id="0bb08-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="0bb08-111">Se `num2` , no exemplo anterior, fosse um campo de uma classe em vez de uma variável local em um procedimento, a declaração causaria um erro com `Option Strict` on e classificaria `num2` como `Object` `Option Strict` off.</span><span class="sxs-lookup"><span data-stu-id="0bb08-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="0bb08-112">Da mesma forma, a inferência de tipo local não se aplica a variáveis de nível de procedimento declaradas como `Static` .</span><span class="sxs-lookup"><span data-stu-id="0bb08-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>

## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="0bb08-113">Inferência de tipos versus associação tardia</span><span class="sxs-lookup"><span data-stu-id="0bb08-113">Type Inference vs. Late Binding</span></span>

<span data-ttu-id="0bb08-114">O código que usa a inferência de tipos assemelha-se ao código que depende da ligação tardia.</span><span class="sxs-lookup"><span data-stu-id="0bb08-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="0bb08-115">No entanto, a inferência de tipos digita fortemente a variável em vez de deixá-la como `Object` .</span><span class="sxs-lookup"><span data-stu-id="0bb08-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="0bb08-116">O compilador usa o inicializador de uma variável para determinar o tipo da variável em tempo de compilação para produzir código de ligação antecipada.</span><span class="sxs-lookup"><span data-stu-id="0bb08-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="0bb08-117">No exemplo anterior, `num2` , like `num1` , é digitado como um `Integer` .</span><span class="sxs-lookup"><span data-stu-id="0bb08-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>

<span data-ttu-id="0bb08-118">O comportamento das variáveis de ligação antecipada difere do que as variáveis de associação tardia, para as quais o tipo é conhecido somente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0bb08-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="0bb08-119">Saber que o tipo inicialmente habilita o compilador a identificar problemas antes da execução, alocar a memória com precisão e executar outras otimizações.</span><span class="sxs-lookup"><span data-stu-id="0bb08-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="0bb08-120">A ligação antecipada também permite que o Visual Basic IDE (ambiente de desenvolvimento integrado) forneça ajuda IntelliSense sobre os membros de um objeto.</span><span class="sxs-lookup"><span data-stu-id="0bb08-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="0bb08-121">A ligação antecipada também é preferida para o desempenho.</span><span class="sxs-lookup"><span data-stu-id="0bb08-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="0bb08-122">Isso ocorre porque todos os dados armazenados em uma variável de associação tardia devem ser encapsulados como tipo `Object` e o acesso a membros do tipo em tempo de execução torna o programa mais lento.</span><span class="sxs-lookup"><span data-stu-id="0bb08-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>

## <a name="examples"></a><span data-ttu-id="0bb08-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0bb08-123">Examples</span></span>

<span data-ttu-id="0bb08-124">A inferência de tipos ocorre quando uma variável local é declarada sem uma `As` cláusula e inicializada.</span><span class="sxs-lookup"><span data-stu-id="0bb08-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="0bb08-125">O compilador usa o tipo de valor inicial atribuído como o tipo da variável.</span><span class="sxs-lookup"><span data-stu-id="0bb08-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="0bb08-126">Por exemplo, cada uma das linhas de código a seguir declara uma variável do tipo `String` .</span><span class="sxs-lookup"><span data-stu-id="0bb08-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

<span data-ttu-id="0bb08-127">O código a seguir demonstra duas maneiras equivalentes de criar uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="0bb08-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

<span data-ttu-id="0bb08-128">É conveniente usar a inferência de tipos para determinar o tipo de uma variável de controle de loop.</span><span class="sxs-lookup"><span data-stu-id="0bb08-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="0bb08-129">No código a seguir, o compilador infere que `number` é um `Integer` porque `someNumbers2` do exemplo anterior é uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="0bb08-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

<span data-ttu-id="0bb08-130">A inferência de tipo local pode ser usada em `Using` instruções para estabelecer o tipo do nome do recurso, como demonstra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0bb08-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

<span data-ttu-id="0bb08-131">O tipo de uma variável também pode ser deduzido dos valores retornados das funções, como demonstra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0bb08-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="0bb08-132">Ambos `pList1` e `pList2` são matrizes de processos porque `Process.GetProcesses` retorna uma matriz de processos.</span><span class="sxs-lookup"><span data-stu-id="0bb08-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a><span data-ttu-id="0bb08-133">Opção Inferir</span><span class="sxs-lookup"><span data-stu-id="0bb08-133">Option Infer</span></span>

<span data-ttu-id="0bb08-134">`Option Infer`permite que você especifique se a inferência de tipo local é permitida em um arquivo específico.</span><span class="sxs-lookup"><span data-stu-id="0bb08-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="0bb08-135">Para habilitar ou bloquear a opção, digite uma das instruções a seguir no início do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0bb08-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>

`Option Infer On`

`Option Infer Off`

<span data-ttu-id="0bb08-136">Se você não especificar um valor para `Option Infer` em seu código, o padrão do compilador será `Option Infer On` .</span><span class="sxs-lookup"><span data-stu-id="0bb08-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span>

<span data-ttu-id="0bb08-137">Se o valor definido para `Option Infer` em um arquivo entrar em conflito com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.</span><span class="sxs-lookup"><span data-stu-id="0bb08-137">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="0bb08-138">Para obter mais informações, consulte [instrução Option Infer](../../../language-reference/statements/option-infer-statement.md) e a [página de compilação, designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0bb08-138">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bb08-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="0bb08-139">See also</span></span>

- [<span data-ttu-id="0bb08-140">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="0bb08-140">Anonymous Types</span></span>](../objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="0bb08-141">Associação antecipada e tardia</span><span class="sxs-lookup"><span data-stu-id="0bb08-141">Early and Late Binding</span></span>](../early-late-binding/index.md)
- [<span data-ttu-id="0bb08-142">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="0bb08-142">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="0bb08-143">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="0bb08-143">For...Next Statement</span></span>](../../../language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="0bb08-144">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="0bb08-144">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="0bb08-145">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="0bb08-145">-optioninfer</span></span>](../../../reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="0bb08-146">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bb08-146">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
