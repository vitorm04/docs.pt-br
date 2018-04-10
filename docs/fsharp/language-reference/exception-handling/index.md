---
title: Tratamento de exceções (F#)
description: 'Conheça os fundamentos da manipulação de exceção no F # e encontrar links para expressões e funções de manipulação de exceção.'
keywords: visual f#, f#, programação funcional
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling"></a><span data-ttu-id="b6447-104">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="b6447-104">Exception Handling</span></span>

<span data-ttu-id="b6447-105">Esta seção contém informações sobre suporte à manipulação de exceção na linguagem F#.</span><span class="sxs-lookup"><span data-stu-id="b6447-105">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="b6447-106">Noções básicas do tratamento de exceção</span><span class="sxs-lookup"><span data-stu-id="b6447-106">Exception Handling Basics</span></span>
<span data-ttu-id="b6447-107">O tratamento de exceção é a maneira padrão de lidar com condições de erro no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6447-107">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="b6447-108">Portanto, qualquer linguagem .NET deve oferecer suporte a esse mecanismo, incluindo F#.</span><span class="sxs-lookup"><span data-stu-id="b6447-108">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="b6447-109">Um *exceção* é um objeto que encapsula informações sobre um erro.</span><span class="sxs-lookup"><span data-stu-id="b6447-109">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="b6447-110">Quando ocorrem erros, as exceções são acionadas e a execução normal é interrompida.</span><span class="sxs-lookup"><span data-stu-id="b6447-110">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="b6447-111">Em vez disso, o tempo de execução procura um manipulador apropriado para a exceção.</span><span class="sxs-lookup"><span data-stu-id="b6447-111">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="b6447-112">A pesquisa começa na função atual e continua na pilha passando pelas camadas de chamadores até que um manipulador correspondente é encontrado.</span><span class="sxs-lookup"><span data-stu-id="b6447-112">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="b6447-113">Em seguida, o manipulador é executado.</span><span class="sxs-lookup"><span data-stu-id="b6447-113">Then the handler is executed.</span></span>

<span data-ttu-id="b6447-114">Além disso, à medida que a pilha é liberada, o tempo de execução executa qualquer código nos blocos `finally` para garantir que os objetos sejam limpos corretamente durante o processo de liberação.</span><span class="sxs-lookup"><span data-stu-id="b6447-114">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="b6447-115">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="b6447-115">Related Topics</span></span>

|<span data-ttu-id="b6447-116">Título</span><span class="sxs-lookup"><span data-stu-id="b6447-116">Title</span></span>|<span data-ttu-id="b6447-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6447-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="b6447-118">Tipos de Exceção</span><span class="sxs-lookup"><span data-stu-id="b6447-118">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="b6447-119">Descreve como declarar um tipo de exceção.</span><span class="sxs-lookup"><span data-stu-id="b6447-119">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="b6447-120">Exceções: a expressão `try...with`</span><span class="sxs-lookup"><span data-stu-id="b6447-120">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="b6447-121">Descreve a construção de linguagem que oferece suporte à manipulação da exceção.</span><span class="sxs-lookup"><span data-stu-id="b6447-121">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="b6447-122">Exceções: a expressão `try...finally`</span><span class="sxs-lookup"><span data-stu-id="b6447-122">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="b6447-123">Descreve a construção de linguagem que permite a execução do código de limpeza conforme a pilha é liberada quando uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="b6447-123">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="b6447-124">Exceções: a função `raise`</span><span class="sxs-lookup"><span data-stu-id="b6447-124">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="b6447-125">Descreve como lançar um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="b6447-125">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="b6447-126">Exceções: a função `failwith`</span><span class="sxs-lookup"><span data-stu-id="b6447-126">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="b6447-127">Descreve como gerar uma exceção geral do F#.</span><span class="sxs-lookup"><span data-stu-id="b6447-127">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="b6447-128">Exceções: a função `invalidArg`</span><span class="sxs-lookup"><span data-stu-id="b6447-128">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="b6447-129">Descreve como gerar uma exceção de argumento inválido.</span><span class="sxs-lookup"><span data-stu-id="b6447-129">Describes how to generate an invalid argument exception.</span></span>|
