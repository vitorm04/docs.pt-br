---
title: "Criando árvores de expressão"
description: "Saiba mais sobre técnicas de criação de árvores de expressão."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c0d7bcf6e07f4a49e15e6f6f4e028eebfe82d8bf
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="building-expression-trees"></a><span data-ttu-id="6ea16-104">Criando árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="6ea16-104">Building Expression Trees</span></span>

[<span data-ttu-id="6ea16-105">Anterior – Interpretando expressões</span><span class="sxs-lookup"><span data-stu-id="6ea16-105">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="6ea16-106">Todas as árvores de expressão que você viu até agora foram criadas pelo compilador C#.</span><span class="sxs-lookup"><span data-stu-id="6ea16-106">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="6ea16-107">Tudo que eu tive que fazer foi criar uma expressão lambda que foi atribuída a uma variável tipada como um `Expression<Func<T>>` ou algum tipo semelhante.</span><span class="sxs-lookup"><span data-stu-id="6ea16-107">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="6ea16-108">Essa não é a única maneira de criar uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="6ea16-108">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="6ea16-109">Para muitos cenários, você pode descobrir que precisa criar uma expressão na memória em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6ea16-109">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="6ea16-110">Criar árvores de expressão é complicado pelo fato de que essas árvores de expressão são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="6ea16-110">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="6ea16-111">Ser imutável significa que você precisa criar a árvore de folhas até a raiz.</span><span class="sxs-lookup"><span data-stu-id="6ea16-111">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="6ea16-112">As APIs que você usará para criar as árvores de expressão refletem esse fato: os métodos que você usará para criar um nó usam todos os seus filhos como argumentos.</span><span class="sxs-lookup"><span data-stu-id="6ea16-112">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="6ea16-113">Vejamos alguns exemplos para mostrar as técnicas a você.</span><span class="sxs-lookup"><span data-stu-id="6ea16-113">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="6ea16-114">Criando nós</span><span class="sxs-lookup"><span data-stu-id="6ea16-114">Creating Nodes</span></span>

<span data-ttu-id="6ea16-115">Vamos começar de forma relativamente simples mais uma vez.</span><span class="sxs-lookup"><span data-stu-id="6ea16-115">Let's start relatively simply again.</span></span> <span data-ttu-id="6ea16-116">Vamos usar a expressão de adição com que tenho trabalhado durante essas seções:</span><span class="sxs-lookup"><span data-stu-id="6ea16-116">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="6ea16-117">Para construir essa árvore de expressão, você precisará criar os nós de folha.</span><span class="sxs-lookup"><span data-stu-id="6ea16-117">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="6ea16-118">Os nós de folha são constantes, de modo que você pode usar o método `Expression.Constant` para criar os nós:</span><span class="sxs-lookup"><span data-stu-id="6ea16-118">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="6ea16-119">Em seguida, você criará a expressão de adição:</span><span class="sxs-lookup"><span data-stu-id="6ea16-119">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="6ea16-120">Depois que tiver a expressão de adição, você pode criar a expressão lambda:</span><span class="sxs-lookup"><span data-stu-id="6ea16-120">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lamdba = Expression.Lambda(addition);
```

<span data-ttu-id="6ea16-121">Trata-se de uma LambdaExpression muito simples, pois não contém argumentos.</span><span class="sxs-lookup"><span data-stu-id="6ea16-121">This is a very simple LambdaExpression, because it contains no arguments.</span></span>
<span data-ttu-id="6ea16-122">Posteriormente nesta seção, você verá como mapear argumentos para parâmetros e criar expressões mais complicadas.</span><span class="sxs-lookup"><span data-stu-id="6ea16-122">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="6ea16-123">Para expressões que são simples como essa, você pode combinar todas as chamadas em uma única instrução:</span><span class="sxs-lookup"><span data-stu-id="6ea16-123">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="6ea16-124">Criando uma árvore</span><span class="sxs-lookup"><span data-stu-id="6ea16-124">Building a Tree</span></span>

<span data-ttu-id="6ea16-125">Estes são os conceitos básicos da criação de uma árvore de expressão na memória.</span><span class="sxs-lookup"><span data-stu-id="6ea16-125">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="6ea16-126">Árvores mais complexas geralmente significam mais tipos de nó e mais nós na árvore.</span><span class="sxs-lookup"><span data-stu-id="6ea16-126">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="6ea16-127">Vamos percorrer mais um exemplo e mostrar dois outros tipos de nó que você normalmente criará quando criar árvores de expressão: os nós de argumento e os nós de chamada de método.</span><span class="sxs-lookup"><span data-stu-id="6ea16-127">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="6ea16-128">Vamos criar uma árvore de expressão para criar esta expressão:</span><span class="sxs-lookup"><span data-stu-id="6ea16-128">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="6ea16-129">Você começará criando expressões de parâmetro para `x` e `y`:</span><span class="sxs-lookup"><span data-stu-id="6ea16-129">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="6ea16-130">A criação de expressões de multiplicação e adição segue o padrão que você já viu:</span><span class="sxs-lookup"><span data-stu-id="6ea16-130">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="6ea16-131">Em seguida, você precisa criar uma expressão de chamada de método para a chamada para `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="6ea16-131">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="6ea16-132">Depois, por fim, você coloca a chamada de método em uma expressão lambda e define os argumentos para a expressão lambda:</span><span class="sxs-lookup"><span data-stu-id="6ea16-132">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="6ea16-133">Neste exemplo mais complicado, você verá mais algumas técnicas de que frequentemente precisará para criar árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="6ea16-133">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="6ea16-134">Primeiro, você precisa criar os objetos que representam parâmetros ou variáveis locais antes de usá-los.</span><span class="sxs-lookup"><span data-stu-id="6ea16-134">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="6ea16-135">Após ter criado esses objetos, você pode usá-los em sua árvore de expressão quando for necessário.</span><span class="sxs-lookup"><span data-stu-id="6ea16-135">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="6ea16-136">Depois, você precisa usar um subconjunto das APIs de reflexão para criar um objeto `MethodInfo` para que possa criar uma árvore de expressão para acessar esse método.</span><span class="sxs-lookup"><span data-stu-id="6ea16-136">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="6ea16-137">Você deve se limitar ao subconjunto das APIs de reflexão que estão disponíveis na plataforma do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ea16-137">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="6ea16-138">Mais uma vez, essas técnicas se estenderão a outras árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="6ea16-138">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="6ea16-139">Criando código profundamente</span><span class="sxs-lookup"><span data-stu-id="6ea16-139">Building Code In Depth</span></span>

<span data-ttu-id="6ea16-140">Você não fica limitado ao que pode criar usando essas APIs.</span><span class="sxs-lookup"><span data-stu-id="6ea16-140">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="6ea16-141">No entanto, quanto mais complicada for a árvore de expressão que você quer criar, mais difícil ser;a gerenciar e ler o código.</span><span class="sxs-lookup"><span data-stu-id="6ea16-141">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="6ea16-142">Vamos criar uma árvore de expressão que é o equivalente a este código:</span><span class="sxs-lookup"><span data-stu-id="6ea16-142">Let's build an expression tree that is the equivalent of this code:</span></span>

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

<span data-ttu-id="6ea16-143">Acima, observe que eu não criei a árvore de expressão, apenas o delegado.</span><span class="sxs-lookup"><span data-stu-id="6ea16-143">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="6ea16-144">Usando a classe `Expression`, não é possível criar lambdas de instrução.</span><span class="sxs-lookup"><span data-stu-id="6ea16-144">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="6ea16-145">Este é o código que é necessário para criar a mesma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="6ea16-145">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="6ea16-146">Ele é complicado pelo fato de que não há uma API para criar um loop `while`. Em vez disso, você precisa criar um loop que contém um teste condicional e um destino para o rótulo para interromper o loop.</span><span class="sxs-lookup"><span data-stu-id="6ea16-146">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

<span data-ttu-id="6ea16-147">O código para criar a árvore de expressão para a função fatorial é bem mais longo, mais complicado e está cheio de rótulos e instruções de interrupção, bem como outros elementos que gostamos de evitar em nossas tarefas de codificação cotidianas.</span><span class="sxs-lookup"><span data-stu-id="6ea16-147">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="6ea16-148">Para esta seção, também atualizei o código de visitante para visitar cada nó nessa árvore de expressão e gravar informações sobre os nós que são criados neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="6ea16-148">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="6ea16-149">Você pode [exibir ou baixar o código de exemplo](https://github.com/dotnet/docs/tree/master/samples/csharp/expression-trees) no repositório dotnet/docs do GitHub.</span><span class="sxs-lookup"><span data-stu-id="6ea16-149">You can [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="6ea16-150">Experimente por conta própria criando e executando os exemplos.</span><span class="sxs-lookup"><span data-stu-id="6ea16-150">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="6ea16-151">Para obter instruções de download, consulte [Exemplos e tutoriais](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="6ea16-151">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="6ea16-152">Examinando as APIs</span><span class="sxs-lookup"><span data-stu-id="6ea16-152">Examining the APIs</span></span>

<span data-ttu-id="6ea16-153">As APIs de árvore de expressão são algumas das mais difíceis de navegar no .NET Core, mas não tem problema.</span><span class="sxs-lookup"><span data-stu-id="6ea16-153">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="6ea16-154">Sua finalidade é uma tarefa bastante complexa: escrever código que gera código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6ea16-154">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="6ea16-155">Eles são necessariamente complicadas para fornecer um equilíbrio entre dar suporte a todas as estruturas de controle disponíveis na linguagem C# e manter a área de superfície das APIs tão pequena quanto for razoável.</span><span class="sxs-lookup"><span data-stu-id="6ea16-155">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="6ea16-156">Esse equilíbrio significa que muitas estruturas de controle são representadas não por seus constructos em C#, mas por constructos que representam a lógica subjacente que o compilador gera desses constructos de nível superior.</span><span class="sxs-lookup"><span data-stu-id="6ea16-156">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="6ea16-157">Além disso, no momento, há expressões de C# que não podem ser criadas diretamente usando os métodos de classe `Expression`.</span><span class="sxs-lookup"><span data-stu-id="6ea16-157">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="6ea16-158">Em geral, esses serão os operadores e expressões mais novos adicionadas no C# 5 e no C# 6.</span><span class="sxs-lookup"><span data-stu-id="6ea16-158">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="6ea16-159">(Por exemplo, expressões `async` não podem ser criadas e o novo operador `?.` não pode ser criado diretamente.)</span><span class="sxs-lookup"><span data-stu-id="6ea16-159">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="6ea16-160">Próximo – Traduzindo expressões</span><span class="sxs-lookup"><span data-stu-id="6ea16-160">Next -- Translating Expressions</span></span>](expression-trees-translating.md)

