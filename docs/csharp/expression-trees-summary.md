---
title: "Resumo de árvores de expressão"
description: "Recapitula como é possível usar as árvores de expressão para criar programas dinâmicos que interpretam o código como dados e criam uma nova funcionalidade com base nesse código."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: d2754493c782c2550a8b0bd0de274cb8100c78af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="expression-trees-summary"></a><span data-ttu-id="687d0-104">Resumo de árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="687d0-104">Expression Trees Summary</span></span>

[<span data-ttu-id="687d0-105">Anterior – Movendo expressões</span><span class="sxs-lookup"><span data-stu-id="687d0-105">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="687d0-106">Nesta série, você viu como é possível usar as *árvores de expressão* para criar programas dinâmicos que interpretam o código como dados e criam uma nova funcionalidade com base nesse código.</span><span class="sxs-lookup"><span data-stu-id="687d0-106">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="687d0-107">Você pode examinar as árvores de expressão para entender a intenção de um algoritmo.</span><span class="sxs-lookup"><span data-stu-id="687d0-107">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="687d0-108">E não apenas examinar esse código.</span><span class="sxs-lookup"><span data-stu-id="687d0-108">You can not only examine that code.</span></span> <span data-ttu-id="687d0-109">Você pode criar novas árvores de expressão que representam versões modificadas do código original.</span><span class="sxs-lookup"><span data-stu-id="687d0-109">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="687d0-110">E também pode usar as árvores de expressão para examinar um algoritmo e mover esse algoritmo para outra linguagem ou ambiente.</span><span class="sxs-lookup"><span data-stu-id="687d0-110">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="687d0-111">Limitações</span><span class="sxs-lookup"><span data-stu-id="687d0-111">Limitations</span></span>

<span data-ttu-id="687d0-112">Há alguns elementos mais recentes da linguagem C# que não se convertem bem em árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="687d0-112">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="687d0-113">As árvores de expressão não podem conter expressões `await` ou expressões lambda `async`.</span><span class="sxs-lookup"><span data-stu-id="687d0-113">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="687d0-114">Muitos dos recursos adicionados na versão 6 do C# não aparecem exatamente como escritos nas árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="687d0-114">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="687d0-115">Em vez disso, os recursos mais recentes serão expostos em árvores de expressões na sintaxe anterior equivalente.</span><span class="sxs-lookup"><span data-stu-id="687d0-115">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="687d0-116">Isso pode não ser realmente uma limitação como você imagina.</span><span class="sxs-lookup"><span data-stu-id="687d0-116">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="687d0-117">Na verdade, isso significa que é provável que o seu código, que interpreta árvores de expressão, vai continuar funcionando da mesma forma que quando os novos recursos de linguagem forem introduzidos.</span><span class="sxs-lookup"><span data-stu-id="687d0-117">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="687d0-118">Mesmo com essas limitações, as árvores de expressão permitem criar algoritmos dinâmicos que se apoiam na interpretação e modificação do código que é representado como uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="687d0-118">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="687d0-119">Elas são uma ferramenta poderosa e é um dos recursos do ecossistema do .NET que habilita as avançadas bibliotecas, como o Entity Framework, a realizarem o que fazem.</span><span class="sxs-lookup"><span data-stu-id="687d0-119">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>

