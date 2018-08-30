---
title: Tipos de Framework com suporte a árvores de expressão
description: Saiba mais sobre tipos de estrutura com suporte a árvores de expressão, criando árvores de expressão e técnicas para trabalhar com APIs de árvore de expressão.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 687b521c52c1ca380a12e18469b5f66000049d3c
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934786"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="5e5a2-103">Tipos de Framework com suporte a árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="5e5a2-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="5e5a2-104">Anterior – Árvores de expressão explicadas</span><span class="sxs-lookup"><span data-stu-id="5e5a2-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="5e5a2-105">Há uma grande lista de classes do .NET Core Framework que funcionam com árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="5e5a2-106">Veja a lista completa em <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="5e5a2-107">Em vez de percorrer a lista completa, vamos entender como as classes de estrutura foram projetadas.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="5e5a2-108">No design de linguagem, uma expressão é um corpo de código que calcula e retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="5e5a2-109">As expressões podem ser muito simples: a expressão constante `1` retorna o valor constante de 1.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="5e5a2-110">Elas podem ser mais complicados: a expressão `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` retorna uma raiz de uma equação quadrática (no caso em que a equação tem uma solução).</span><span class="sxs-lookup"><span data-stu-id="5e5a2-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="5e5a2-111">Tudo começa com System.Linq.Expression</span><span class="sxs-lookup"><span data-stu-id="5e5a2-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="5e5a2-112">Uma das complexidades de se trabalhar com árvores de expressão é que muitos tipos diferentes de expressões são válidos em muitos locais nos programas.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="5e5a2-113">Considere uma expressão de atribuição.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-113">Consider an assignment expression.</span></span> <span data-ttu-id="5e5a2-114">O lado direito de uma atribuição pode ser um valor constante, uma variável, uma expressão de chamada de método ou outros.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="5e5a2-115">Essa flexibilidade de linguagem significa que você poderá encontrar muitos tipos diferentes de expressão em qualquer lugar nos nós de uma árvore ao percorrer uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="5e5a2-116">Portanto, a maneira mais simples de se trabalhar é quando você pode trabalhar com o tipo de expressão de base.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="5e5a2-117">No entanto, às vezes você precisa saber mais.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="5e5a2-118">A classe Expressão de base contém uma propriedade `NodeType` para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="5e5a2-119">Ela retorna um `ExpressionType` que é uma enumeração dos tipos de expressão possíveis.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="5e5a2-120">Uma vez que você souber qual o tipo do nó, poderá convertê-la para esse tipo e executar ações específicas, conhecendo o tipo do nó de expressão.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="5e5a2-121">Você pode pesquisar determinados tipos de nó e trabalhar com as propriedades específicas desse tipo de expressão.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="5e5a2-122">Por exemplo, esse código imprimirá o nome de uma variável para uma expressão de acesso variável.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="5e5a2-123">Eu segui a prática de verificar o tipo de nó, converter em uma expressão de acesso variável e verificar as propriedades do tipo de expressão específico:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a><span data-ttu-id="5e5a2-124">Criando árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="5e5a2-124">Creating Expression Trees</span></span>

<span data-ttu-id="5e5a2-125">A classe `System.Linq.Expression` também contém vários métodos estáticos para criar expressões.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="5e5a2-126">Esses métodos criam um nó de expressão usando os argumentos fornecidos para seus filhos.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="5e5a2-127">Dessa forma, você cria uma expressão de seus nós folha.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="5e5a2-128">Por exemplo, esse código cria uma expressão de Adicionar:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="5e5a2-129">Você pode ver neste exemplo simples que há muitos tipos envolvidos na criação e no trabalho com árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="5e5a2-130">Essa complexidade é necessária para fornecer os recursos do vocabulário avançado fornecido pela linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="5e5a2-131">Navegando nas APIs</span><span class="sxs-lookup"><span data-stu-id="5e5a2-131">Navigating the APIs</span></span>
<span data-ttu-id="5e5a2-132">Há tipos de Nó de expressão que mapeiam para quase todos os elementos de sintaxe da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="5e5a2-133">Cada tipo tem métodos específicos para esse tipo de elemento de linguagem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="5e5a2-134">É muita coisa para guardar na memória ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="5e5a2-135">Em vez de tentar memorizar tudo, aqui estão as técnicas que eu uso para trabalhar com Árvores de expressão:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="5e5a2-136">Observar os membros da enumeração `ExpressionType` para determinar possíveis nós que devem ser examinados.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="5e5a2-137">Isso é realmente útil se você deseja percorrer e entender uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="5e5a2-138">Observar os membros estáticos da classe `Expression` para compilar uma expressão.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="5e5a2-139">Esses métodos podem compilar qualquer tipo de expressão em um conjunto de seu nós filho.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="5e5a2-140">Examinar a classe `ExpressionVisitor` para compilar uma árvore de expressão modificada.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="5e5a2-141">Você encontrará mais ao examinar cada uma dessas três áreas.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="5e5a2-142">Invariavelmente, você encontrará o que precisa ao começar com uma dessas três etapas.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="5e5a2-143">Próximo – Executar árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="5e5a2-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
 
