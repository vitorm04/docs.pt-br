---
title: Instruções em C# - um tour pela linguagem C#
description: Criar as ações de um programa em C# usando as instruções
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 75f6c7bb29af7f9c809c5278c97d21683166a8e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154288"
---
# <a name="statements"></a><span data-ttu-id="7f85d-103">Instruções</span><span class="sxs-lookup"><span data-stu-id="7f85d-103">Statements</span></span>

<span data-ttu-id="7f85d-104">As ações de um programa são expressas usando *instruções*.</span><span class="sxs-lookup"><span data-stu-id="7f85d-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="7f85d-105">O C# oferece suporte a vários tipos diferentes de instruções, algumas delas definidas em termos de instruções inseridas.</span><span class="sxs-lookup"><span data-stu-id="7f85d-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="7f85d-106">Um *bloco* permite a produção de várias instruções em contextos nos quais uma única instrução é permitida.</span><span class="sxs-lookup"><span data-stu-id="7f85d-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="7f85d-107">Um bloco é composto por uma lista de instruções escritas entre os delimitadores `{` e `}`.</span><span class="sxs-lookup"><span data-stu-id="7f85d-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="7f85d-108">*Instruções de declaração* são usadas para declarar constantes e variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="7f85d-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="7f85d-109">*Instruções de expressão* são usadas para avaliar expressões.</span><span class="sxs-lookup"><span data-stu-id="7f85d-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="7f85d-110">As expressões que podem ser usadas como instruções incluem chamadas de método, alocações de objeto usando o operador `new`, atribuições usando `=` e os operadores de atribuição compostos, operações de incremento e decremento usando os operadores `++` e `--` e as expressões `await`.</span><span class="sxs-lookup"><span data-stu-id="7f85d-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="7f85d-111">*Instruções de seleção* são usadas para selecionar uma dentre várias instruções possíveis para execução com base no valor de alguma expressão.</span><span class="sxs-lookup"><span data-stu-id="7f85d-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="7f85d-112">Neste grupo estão as instruções `if` e `switch`.</span><span class="sxs-lookup"><span data-stu-id="7f85d-112">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="7f85d-113">*Instruções de iteração* são usadas para executar repetidamente uma instrução inserida.</span><span class="sxs-lookup"><span data-stu-id="7f85d-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="7f85d-114">Neste grupo estão as instruções `while`, `do`, `for` e `foreach`.</span><span class="sxs-lookup"><span data-stu-id="7f85d-114">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="7f85d-115">*Instruções de salto* são usadas para transferir o controle.</span><span class="sxs-lookup"><span data-stu-id="7f85d-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="7f85d-116">Neste grupo estão as instruções `break`, `continue`, `goto`, `throw`, `return` e `yield`.</span><span class="sxs-lookup"><span data-stu-id="7f85d-116">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="7f85d-117">A instrução `try`... `catch` é usada para capturar exceções que ocorrem durante a execução de um bloco, e a instrução `try`... `finally` é usada para especificar o código de finalização que é executado sempre, se uma exceção ocorrer ou não.</span><span class="sxs-lookup"><span data-stu-id="7f85d-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="7f85d-118">As instruções `checked` e `unchecked` são usadas para controlar o contexto de verificação de estouro para operações e conversões aritméticas do tipo integral.</span><span class="sxs-lookup"><span data-stu-id="7f85d-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="7f85d-119">A instrução `lock` é usada para obter o bloqueio de exclusão mútua para um determinado objeto, executar uma instrução e, em seguida, liberar o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7f85d-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="7f85d-120">A instrução `using` é usada para obter um recurso, executar uma instrução e, em seguida, descartar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="7f85d-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="7f85d-121">A lista a seguir contém os tipos de instruções que podem ser usados, e fornece um exemplo para cada um.</span><span class="sxs-lookup"><span data-stu-id="7f85d-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="7f85d-122">Declaração de variável local:</span><span class="sxs-lookup"><span data-stu-id="7f85d-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="7f85d-123">Declaração constante local:</span><span class="sxs-lookup"><span data-stu-id="7f85d-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="7f85d-124">Instrução de expressão:</span><span class="sxs-lookup"><span data-stu-id="7f85d-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="7f85d-125">Instrução `if`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="7f85d-126">Instrução `switch`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="7f85d-127">Instrução `while`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="7f85d-128">Instrução `do`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="7f85d-129">Instrução `for`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="7f85d-130">Instrução `foreach`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="7f85d-131">Instrução `break`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="7f85d-132">Instrução `continue`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="7f85d-133">Instrução `goto`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="7f85d-134">Instrução `return`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="7f85d-135">Instrução `yield`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="7f85d-136">Instruções `throw` e instruções `try`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="7f85d-137">Instruções `checked` e `unchecked`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="7f85d-138">Instrução `lock`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="7f85d-139">Instrução `using`:</span><span class="sxs-lookup"><span data-stu-id="7f85d-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="7f85d-140">[Anterior](expressions.md)
>[Próximo](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="7f85d-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>