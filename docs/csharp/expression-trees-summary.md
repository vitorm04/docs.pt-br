---
title: Resumo de árvores de expressão
description: Recapitula como é possível usar as árvores de expressão para criar programas dinâmicos que interpretam o código como dados e criam uma nova funcionalidade com base nesse código.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 43715c94b70f1cd7f758cde91ae7c8d1b2f70f9f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036749"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="cf526-103">Resumo de árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="cf526-103">Expression Trees Summary</span></span>

[<span data-ttu-id="cf526-104">Anterior – Movendo expressões</span><span class="sxs-lookup"><span data-stu-id="cf526-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="cf526-105">Nesta série, você viu como é possível usar as *árvores de expressão* para criar programas dinâmicos que interpretam o código como dados e criam uma nova funcionalidade com base nesse código.</span><span class="sxs-lookup"><span data-stu-id="cf526-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="cf526-106">Você pode examinar as árvores de expressão para entender a intenção de um algoritmo.</span><span class="sxs-lookup"><span data-stu-id="cf526-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="cf526-107">E não apenas examinar esse código.</span><span class="sxs-lookup"><span data-stu-id="cf526-107">You can not only examine that code.</span></span> <span data-ttu-id="cf526-108">Você pode criar novas árvores de expressão que representam versões modificadas do código original.</span><span class="sxs-lookup"><span data-stu-id="cf526-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="cf526-109">E também pode usar as árvores de expressão para examinar um algoritmo e mover esse algoritmo para outra linguagem ou ambiente.</span><span class="sxs-lookup"><span data-stu-id="cf526-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="cf526-110">Limitações</span><span class="sxs-lookup"><span data-stu-id="cf526-110">Limitations</span></span>

<span data-ttu-id="cf526-111">Há alguns elementos mais recentes da linguagem C# que não se convertem bem em árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="cf526-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="cf526-112">As árvores de expressão não podem conter expressões `await` ou expressões lambda `async`.</span><span class="sxs-lookup"><span data-stu-id="cf526-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="cf526-113">Muitos dos recursos adicionados na versão 6 do C# não aparecem exatamente como escritos nas árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="cf526-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="cf526-114">Em vez disso, os recursos mais recentes serão expostos em árvores de expressões na sintaxe anterior equivalente.</span><span class="sxs-lookup"><span data-stu-id="cf526-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="cf526-115">Isso pode não ser realmente uma limitação como você imagina.</span><span class="sxs-lookup"><span data-stu-id="cf526-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="cf526-116">Na verdade, isso significa que é provável que o seu código, que interpreta árvores de expressão, vai continuar funcionando da mesma forma que quando os novos recursos de linguagem forem introduzidos.</span><span class="sxs-lookup"><span data-stu-id="cf526-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="cf526-117">Mesmo com essas limitações, as árvores de expressão permitem criar algoritmos dinâmicos que se apoiam na interpretação e modificação do código que é representado como uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="cf526-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="cf526-118">Elas são uma ferramenta poderosa e é um dos recursos do ecossistema do .NET que habilita as avançadas bibliotecas, como o Entity Framework, a realizarem o que fazem.</span><span class="sxs-lookup"><span data-stu-id="cf526-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
