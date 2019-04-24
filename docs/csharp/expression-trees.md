---
title: Árvores de expressão
description: Saiba mais sobre árvores de expressão no .NET Core e como usá-las para representar o código como estruturas que você pode examinar, modificar e executar.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db6e23d1ad0014a7dbb58a0cd473e67d6bd9acc0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096606"
---
# <a name="expression-trees"></a><span data-ttu-id="84d82-103">Árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="84d82-103">Expression Trees</span></span>

<span data-ttu-id="84d82-104">Se tiver usado o LINQ, você tem experiência com uma rica biblioteca em que os tipos `Func` fazem parte do conjunto de API.</span><span class="sxs-lookup"><span data-stu-id="84d82-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="84d82-105">(Se você não estiver familiarizado com o LINQ, sugerimos que leia o [tutorial do LINQ](linq/index.md) e o artigo sobre [expressões lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) antes deste). *Árvores de expressão* fornecem uma interação mais avançada com os argumentos que são funções.</span><span class="sxs-lookup"><span data-stu-id="84d82-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="84d82-106">Você escreve argumentos de função, normalmente usando expressões lambda, quando cria consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="84d82-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="84d82-107">Em uma consulta LINQ típica, esses argumentos de função são transformados em um delegado que o compilador cria.</span><span class="sxs-lookup"><span data-stu-id="84d82-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="84d82-108">Quando quiser ter uma interação mais avançada, você precisa usar *Árvores de expressão*.</span><span class="sxs-lookup"><span data-stu-id="84d82-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="84d82-109">Árvores de expressão representam o código como uma estrutura que você pode examinar, modificar ou executar.</span><span class="sxs-lookup"><span data-stu-id="84d82-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="84d82-110">Essas ferramentas oferecem a capacidade de manipular o código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="84d82-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="84d82-111">Você pode escrever código que examina algoritmos em execução ou injeta novos recursos.</span><span class="sxs-lookup"><span data-stu-id="84d82-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="84d82-112">Em cenários mais avançados, você pode modificar algoritmos em execução e até mesmo converter expressões C# para outro formato para execução em outro ambiente.</span><span class="sxs-lookup"><span data-stu-id="84d82-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="84d82-113">Provavelmente, você já escreveu código usando Árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="84d82-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="84d82-114">APIs do LINQ do Entity Framework aceitam Árvores de expressão como os argumentos para o padrão de expressão de consulta do LINQ.</span><span class="sxs-lookup"><span data-stu-id="84d82-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="84d82-115">Isso permite que o [Entity Framework](/ef/) converta a consulta que você escreveu em C# em SQL, que é executado no mecanismo do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="84d82-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="84d82-116">Outro exemplo é [Moq](https://github.com/Moq/moq), que é uma estrutura de simulação popular para .NET.</span><span class="sxs-lookup"><span data-stu-id="84d82-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="84d82-117">As seções restantes deste tutorial explorarão o que são as árvores de expressão, examinarão as classes de estrutura que dão suporte a árvores de expressão e mostrarão como trabalhar com árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="84d82-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="84d82-118">Você aprenderá a ler árvores de expressão, criar árvores de expressão, criar árvores de expressão modificadas e executar o código representado pelas árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="84d82-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="84d82-119">Após a leitura, você estará pronto para usar essas estruturas para criar algoritmos adaptáveis avançados.</span><span class="sxs-lookup"><span data-stu-id="84d82-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="84d82-120">Árvores de Expressão Explicadas</span><span class="sxs-lookup"><span data-stu-id="84d82-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="84d82-121">Compreender a estrutura e os conceitos por trás das *Árvores de Expressão*.</span><span class="sxs-lookup"><span data-stu-id="84d82-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="84d82-122">Tipos de Framework com Suporte a Árvores de Expressão</span><span class="sxs-lookup"><span data-stu-id="84d82-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="84d82-123">Saiba mais sobre as estruturas e classes que definem e manipulam as árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="84d82-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="84d82-124">Executando Expressões</span><span class="sxs-lookup"><span data-stu-id="84d82-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="84d82-125">Saiba como converter uma árvore de expressão representada como uma expressão lambda em um delegado e como executar o delegado resultante.</span><span class="sxs-lookup"><span data-stu-id="84d82-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="84d82-126">Interpretando Expressões</span><span class="sxs-lookup"><span data-stu-id="84d82-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="84d82-127">Saiba como percorrer e examinar *árvores de expressão* para entender que código a árvore de expressão representa.</span><span class="sxs-lookup"><span data-stu-id="84d82-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="84d82-128">Compilando Expressões</span><span class="sxs-lookup"><span data-stu-id="84d82-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="84d82-129">Saiba como construir os nós de uma árvore de expressão e compilar árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="84d82-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="84d82-130">Traduzindo Expressões</span><span class="sxs-lookup"><span data-stu-id="84d82-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="84d82-131">Saiba como compilar uma cópia modificada de uma árvore de expressão ou converter uma árvore de expressão em um formato diferente.</span><span class="sxs-lookup"><span data-stu-id="84d82-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="84d82-132">Resumindo</span><span class="sxs-lookup"><span data-stu-id="84d82-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="84d82-133">Examine informações sobre as árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="84d82-133">Review the information on expression trees.</span></span>
