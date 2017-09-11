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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 99ec2489daf89926da9b8c4e148965412826a8a6
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="statements"></a><span data-ttu-id="ca454-104">Instruções</span><span class="sxs-lookup"><span data-stu-id="ca454-104">Statements</span></span>

<span data-ttu-id="ca454-105">As ações de um programa são expressas usando *instruções*.</span><span class="sxs-lookup"><span data-stu-id="ca454-105">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="ca454-106">O C# oferece suporte a vários tipos diferentes de instruções, algumas delas definidas em termos de instruções inseridas.</span><span class="sxs-lookup"><span data-stu-id="ca454-106">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="ca454-107">Um *bloco* permite a produção de várias instruções em contextos nos quais uma única instrução é permitida.</span><span class="sxs-lookup"><span data-stu-id="ca454-107">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="ca454-108">Um bloco é composto por uma lista de instruções escritas entre os delimitadores `{` e `}`.</span><span class="sxs-lookup"><span data-stu-id="ca454-108">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="ca454-109">*Instruções de declaração* são usadas para declarar constantes e variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="ca454-109">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="ca454-110">*Instruções de expressão* são usadas para avaliar expressões.</span><span class="sxs-lookup"><span data-stu-id="ca454-110">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="ca454-111">As expressões que podem ser usadas como instruções incluem chamadas de método, alocações de objeto usando o operador `new`, atribuições usando `=` e os operadores de atribuição compostos, operações de incremento e decremento usando os operadores `++` e `--` e as expressões `await`.</span><span class="sxs-lookup"><span data-stu-id="ca454-111">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="ca454-112">*Instruções de seleção* são usadas para selecionar uma dentre várias instruções possíveis para execução com base no valor de alguma expressão.</span><span class="sxs-lookup"><span data-stu-id="ca454-112">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="ca454-113">Neste grupo estão as instruções `if` e `switch`.</span><span class="sxs-lookup"><span data-stu-id="ca454-113">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="ca454-114">*Instruções de iteração* são usadas para executar repetidamente uma instrução inserida.</span><span class="sxs-lookup"><span data-stu-id="ca454-114">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="ca454-115">Neste grupo estão as instruções `while`, `do`, `for` e `foreach`.</span><span class="sxs-lookup"><span data-stu-id="ca454-115">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="ca454-116">*Instruções de salto* são usadas para transferir o controle.</span><span class="sxs-lookup"><span data-stu-id="ca454-116">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="ca454-117">Neste grupo estão as instruções `break`, `continue`, `goto`, `throw`, `return` e `yield`.</span><span class="sxs-lookup"><span data-stu-id="ca454-117">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="ca454-118">A instrução `try`... `catch` é usada para capturar exceções que ocorrem durante a execução de um bloco, e a instrução `try`... `finally` é usada para especificar o código de finalização que é executado sempre, se uma exceção ocorrer ou não.</span><span class="sxs-lookup"><span data-stu-id="ca454-118">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="ca454-119">As instruções `checked` e `unchecked` são usadas para controlar o contexto de verificação de estouro para operações e conversões aritméticas do tipo integral.</span><span class="sxs-lookup"><span data-stu-id="ca454-119">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="ca454-120">A instrução `lock` é usada para obter o bloqueio de exclusão mútua para um determinado objeto, executar uma instrução e, em seguida, liberar o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ca454-120">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="ca454-121">A instrução `using` é usada para obter um recurso, executar uma instrução e, em seguida, descartar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="ca454-121">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="ca454-122">A lista a seguir contém os tipos de instruções que podem ser usados, e fornece um exemplo para cada um.</span><span class="sxs-lookup"><span data-stu-id="ca454-122">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="ca454-123">Declaração de variável local:</span><span class="sxs-lookup"><span data-stu-id="ca454-123">Local variable declaration:</span></span>

 <span data-ttu-id="ca454-124">[!code-csharp[Declarações](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]</span><span class="sxs-lookup"><span data-stu-id="ca454-124">[!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]</span></span>

* <span data-ttu-id="ca454-125">Declaração constante local:</span><span class="sxs-lookup"><span data-stu-id="ca454-125">Local constant declaration:</span></span>

 <span data-ttu-id="ca454-126">[!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]</span><span class="sxs-lookup"><span data-stu-id="ca454-126">[!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]</span></span>

* <span data-ttu-id="ca454-127">Instrução de expressão:</span><span class="sxs-lookup"><span data-stu-id="ca454-127">Expression statement:</span></span>

 <span data-ttu-id="ca454-128">[!code-csharp[Expressões](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]</span><span class="sxs-lookup"><span data-stu-id="ca454-128">[!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]</span></span>

* <span data-ttu-id="ca454-129">Instrução `if`:</span><span class="sxs-lookup"><span data-stu-id="ca454-129">`if` statement:</span></span>

 <span data-ttu-id="ca454-130">[!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]</span><span class="sxs-lookup"><span data-stu-id="ca454-130">[!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]</span></span>

* <span data-ttu-id="ca454-131">Instrução `switch`:</span><span class="sxs-lookup"><span data-stu-id="ca454-131">`switch` statement:</span></span>

 <span data-ttu-id="ca454-132">[!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]</span><span class="sxs-lookup"><span data-stu-id="ca454-132">[!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]</span></span>

* <span data-ttu-id="ca454-133">Instrução `while`:</span><span class="sxs-lookup"><span data-stu-id="ca454-133">`while` statement:</span></span>

 <span data-ttu-id="ca454-134">[!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]</span><span class="sxs-lookup"><span data-stu-id="ca454-134">[!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]</span></span>

* <span data-ttu-id="ca454-135">Instrução `do`:</span><span class="sxs-lookup"><span data-stu-id="ca454-135">`do` statement:</span></span>

 <span data-ttu-id="ca454-136">[!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]</span><span class="sxs-lookup"><span data-stu-id="ca454-136">[!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]</span></span>

* <span data-ttu-id="ca454-137">Instrução `for`:</span><span class="sxs-lookup"><span data-stu-id="ca454-137">`for` statement:</span></span>

 <span data-ttu-id="ca454-138">[!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]</span><span class="sxs-lookup"><span data-stu-id="ca454-138">[!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]</span></span>

* <span data-ttu-id="ca454-139">Instrução `foreach`:</span><span class="sxs-lookup"><span data-stu-id="ca454-139">`foreach` statement:</span></span>

 <span data-ttu-id="ca454-140">[!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]</span><span class="sxs-lookup"><span data-stu-id="ca454-140">[!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]</span></span>

* <span data-ttu-id="ca454-141">Instrução `break`:</span><span class="sxs-lookup"><span data-stu-id="ca454-141">`break` statement:</span></span>

 <span data-ttu-id="ca454-142">[!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]</span><span class="sxs-lookup"><span data-stu-id="ca454-142">[!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]</span></span>

* <span data-ttu-id="ca454-143">Instrução `continue`:</span><span class="sxs-lookup"><span data-stu-id="ca454-143">`continue` statement:</span></span>

 <span data-ttu-id="ca454-144">[!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]</span><span class="sxs-lookup"><span data-stu-id="ca454-144">[!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]</span></span>

* <span data-ttu-id="ca454-145">Instrução `goto`:</span><span class="sxs-lookup"><span data-stu-id="ca454-145">`goto` statement:</span></span>

 <span data-ttu-id="ca454-146">[!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]</span><span class="sxs-lookup"><span data-stu-id="ca454-146">[!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]</span></span>

* <span data-ttu-id="ca454-147">Instrução `return`:</span><span class="sxs-lookup"><span data-stu-id="ca454-147">`return` statement:</span></span>

 <span data-ttu-id="ca454-148">[!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]</span><span class="sxs-lookup"><span data-stu-id="ca454-148">[!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]</span></span>

* <span data-ttu-id="ca454-149">Instrução `yield`:</span><span class="sxs-lookup"><span data-stu-id="ca454-149">`yield` statement:</span></span>

 <span data-ttu-id="ca454-150">[!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]</span><span class="sxs-lookup"><span data-stu-id="ca454-150">[!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]</span></span>

* <span data-ttu-id="ca454-151">Instruções `throw` e instruções `try`:</span><span class="sxs-lookup"><span data-stu-id="ca454-151">`throw` statements and `try` statements:</span></span>

 <span data-ttu-id="ca454-152">[!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]</span><span class="sxs-lookup"><span data-stu-id="ca454-152">[!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]</span></span>

* <span data-ttu-id="ca454-153">Instruções `checked` e `unchecked`:</span><span class="sxs-lookup"><span data-stu-id="ca454-153">`checked` and `unchecked` statements:</span></span>

 <span data-ttu-id="ca454-154">[!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]</span><span class="sxs-lookup"><span data-stu-id="ca454-154">[!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]</span></span>

* <span data-ttu-id="ca454-155">Instrução `lock`:</span><span class="sxs-lookup"><span data-stu-id="ca454-155">`lock` statement:</span></span>

 <span data-ttu-id="ca454-156">[!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]</span><span class="sxs-lookup"><span data-stu-id="ca454-156">[!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]</span></span>

* <span data-ttu-id="ca454-157">Instrução `using`:</span><span class="sxs-lookup"><span data-stu-id="ca454-157">`using` statement:</span></span>

 <span data-ttu-id="ca454-158">[!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]</span><span class="sxs-lookup"><span data-stu-id="ca454-158">[!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="ca454-159">[Anterior](expressions.md)
[Próximo](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="ca454-159">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>

