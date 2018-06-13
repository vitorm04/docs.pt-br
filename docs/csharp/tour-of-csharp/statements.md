---
title: Instruções em C# - um tour pela linguagem C#
description: Criar as ações de um programa em C# usando as instruções
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 2f25c07ccc0af27a503465b9414bf607c61d1b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351973"
---
# <a name="statements"></a>Instruções

As ações de um programa são expressas usando *instruções*. O C# oferece suporte a vários tipos diferentes de instruções, algumas delas definidas em termos de instruções inseridas.

Um *bloco* permite a produção de várias instruções em contextos nos quais uma única instrução é permitida. Um bloco é composto por uma lista de instruções escritas entre os delimitadores `{` e `}`.

*Instruções de declaração* são usadas para declarar constantes e variáveis locais.

*Instruções de expressão* são usadas para avaliar expressões. As expressões que podem ser usadas como instruções incluem chamadas de método, alocações de objeto usando o operador `new`, atribuições usando `=` e os operadores de atribuição compostos, operações de incremento e decremento usando os operadores `++` e `--` e as expressões `await`.

*Instruções de seleção* são usadas para selecionar uma dentre várias instruções possíveis para execução com base no valor de alguma expressão. Neste grupo estão as instruções `if` e `switch`.

*Instruções de iteração* são usadas para executar repetidamente uma instrução inserida. Neste grupo estão as instruções `while`, `do`, `for` e `foreach`.

*Instruções de salto* são usadas para transferir o controle. Neste grupo estão as instruções `break`, `continue`, `goto`, `throw`, `return` e `yield`.

A instrução `try`... `catch` é usada para capturar exceções que ocorrem durante a execução de um bloco, e a instrução `try`... `finally` é usada para especificar o código de finalização que é executado sempre, se uma exceção ocorrer ou não.

As instruções `checked` e `unchecked` são usadas para controlar o contexto de verificação de estouro para operações e conversões aritméticas do tipo integral.

A instrução `lock` é usada para obter o bloqueio de exclusão mútua para um determinado objeto, executar uma instrução e, em seguida, liberar o bloqueio.

A instrução `using` é usada para obter um recurso, executar uma instrução e, em seguida, descartar esse recurso.

A lista a seguir contém os tipos de instruções que podem ser usados, e fornece um exemplo para cada um.

* Declaração de variável local:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Declaração constante local:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* Instrução de expressão:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* Instrução `if`:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* Instrução `switch`:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* Instrução `while`:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* Instrução `do`:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* Instrução `for`:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* Instrução `foreach`:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* Instrução `break`:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* Instrução `continue`:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* Instrução `goto`:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* Instrução `return`:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* Instrução `yield`:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* Instruções `throw` e instruções `try`:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* Instruções `checked` e `unchecked`:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* Instrução `lock`:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* Instrução `using`:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
[Anterior](expressions.md)
[Próximo](classes-and-objects.md)
