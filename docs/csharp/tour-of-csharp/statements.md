---
title: "Instruções em C# - um tour pela linguagem C#"
description: "Criar as ações de um programa em C# usando as instruções"
keywords: ".NET, csharp, instruções, sintaxe"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 99ec2489daf89926da9b8c4e148965412826a8a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="statements"></a><span data-ttu-id="328c0-104">Instruções</span><span class="sxs-lookup"><span data-stu-id="328c0-104">Statements</span></span>

<span data-ttu-id="328c0-105">As ações de um programa são expressas usando *instruções*.</span><span class="sxs-lookup"><span data-stu-id="328c0-105">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="328c0-106">O C# oferece suporte a vários tipos diferentes de instruções, algumas delas definidas em termos de instruções inseridas.</span><span class="sxs-lookup"><span data-stu-id="328c0-106">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="328c0-107">Um *bloco* permite a produção de várias instruções em contextos nos quais uma única instrução é permitida.</span><span class="sxs-lookup"><span data-stu-id="328c0-107">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="328c0-108">Um bloco é composto por uma lista de instruções escritas entre os delimitadores `{` e `}`.</span><span class="sxs-lookup"><span data-stu-id="328c0-108">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="328c0-109">*Instruções de declaração* são usadas para declarar constantes e variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="328c0-109">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="328c0-110">*Instruções de expressão* são usadas para avaliar expressões.</span><span class="sxs-lookup"><span data-stu-id="328c0-110">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="328c0-111">As expressões que podem ser usadas como instruções incluem chamadas de método, alocações de objeto usando o operador `new`, atribuições usando `=` e os operadores de atribuição compostos, operações de incremento e decremento usando os operadores `++` e `--` e as expressões `await`.</span><span class="sxs-lookup"><span data-stu-id="328c0-111">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="328c0-112">*Instruções de seleção* são usadas para selecionar uma dentre várias instruções possíveis para execução com base no valor de alguma expressão.</span><span class="sxs-lookup"><span data-stu-id="328c0-112">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="328c0-113">Neste grupo estão as instruções `if` e `switch`.</span><span class="sxs-lookup"><span data-stu-id="328c0-113">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="328c0-114">*Instruções de iteração* são usadas para executar repetidamente uma instrução inserida.</span><span class="sxs-lookup"><span data-stu-id="328c0-114">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="328c0-115">Neste grupo estão as instruções `while`, `do`, `for` e `foreach`.</span><span class="sxs-lookup"><span data-stu-id="328c0-115">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="328c0-116">*Instruções de salto* são usadas para transferir o controle.</span><span class="sxs-lookup"><span data-stu-id="328c0-116">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="328c0-117">Neste grupo estão as instruções `break`, `continue`, `goto`, `throw`, `return` e `yield`.</span><span class="sxs-lookup"><span data-stu-id="328c0-117">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="328c0-118">A instrução `try`... `catch` é usada para capturar exceções que ocorrem durante a execução de um bloco, e a instrução `try`... `finally` é usada para especificar o código de finalização que é executado sempre, se uma exceção ocorrer ou não.</span><span class="sxs-lookup"><span data-stu-id="328c0-118">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="328c0-119">As instruções `checked` e `unchecked` são usadas para controlar o contexto de verificação de estouro para operações e conversões aritméticas do tipo integral.</span><span class="sxs-lookup"><span data-stu-id="328c0-119">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="328c0-120">A instrução `lock` é usada para obter o bloqueio de exclusão mútua para um determinado objeto, executar uma instrução e, em seguida, liberar o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="328c0-120">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="328c0-121">A instrução `using` é usada para obter um recurso, executar uma instrução e, em seguida, descartar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="328c0-121">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="328c0-122">A lista a seguir contém os tipos de instruções que podem ser usados, e fornece um exemplo para cada um.</span><span class="sxs-lookup"><span data-stu-id="328c0-122">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="328c0-123">Declaração de variável local:</span><span class="sxs-lookup"><span data-stu-id="328c0-123">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="328c0-124">Declaração constante local:</span><span class="sxs-lookup"><span data-stu-id="328c0-124">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="328c0-125">Instrução de expressão:</span><span class="sxs-lookup"><span data-stu-id="328c0-125">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="328c0-126">Instrução `if`:</span><span class="sxs-lookup"><span data-stu-id="328c0-126">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="328c0-127">Instrução `switch`:</span><span class="sxs-lookup"><span data-stu-id="328c0-127">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="328c0-128">Instrução `while`:</span><span class="sxs-lookup"><span data-stu-id="328c0-128">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="328c0-129">Instrução `do`:</span><span class="sxs-lookup"><span data-stu-id="328c0-129">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="328c0-130">Instrução `for`:</span><span class="sxs-lookup"><span data-stu-id="328c0-130">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="328c0-131">Instrução `foreach`:</span><span class="sxs-lookup"><span data-stu-id="328c0-131">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="328c0-132">Instrução `break`:</span><span class="sxs-lookup"><span data-stu-id="328c0-132">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="328c0-133">Instrução `continue`:</span><span class="sxs-lookup"><span data-stu-id="328c0-133">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="328c0-134">Instrução `goto`:</span><span class="sxs-lookup"><span data-stu-id="328c0-134">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="328c0-135">Instrução `return`:</span><span class="sxs-lookup"><span data-stu-id="328c0-135">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="328c0-136">Instrução `yield`:</span><span class="sxs-lookup"><span data-stu-id="328c0-136">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="328c0-137">Instruções `throw` e instruções `try`:</span><span class="sxs-lookup"><span data-stu-id="328c0-137">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="328c0-138">Instruções `checked` e `unchecked`:</span><span class="sxs-lookup"><span data-stu-id="328c0-138">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="328c0-139">Instrução `lock`:</span><span class="sxs-lookup"><span data-stu-id="328c0-139">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="328c0-140">Instrução `using`:</span><span class="sxs-lookup"><span data-stu-id="328c0-140">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
<span data-ttu-id="328c0-141">[Anterior](expressions.md)
[Próximo](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="328c0-141">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
