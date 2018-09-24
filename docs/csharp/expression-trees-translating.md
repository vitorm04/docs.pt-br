---
title: Movendo árvores de expressão
description: Aprenda a visitar cada nó em uma árvore de expressão, enquanto estiver criando uma cópia modificada dessa árvore de expressão.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: bd4aec2ef34e4dc972ae867c6b5070f92dcbc498
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45971886"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="8e4a2-103">Movendo árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="8e4a2-103">Translating Expression Trees</span></span>

[<span data-ttu-id="8e4a2-104">Anterior – Compilando expressões</span><span class="sxs-lookup"><span data-stu-id="8e4a2-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="8e4a2-105">Nesta seção final, você aprenderá a visitar cada nó em uma árvore de expressão, enquanto estiver criando uma cópia modificada dessa árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="8e4a2-106">Essas são as técnicas que você usará em dois cenários importantes.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="8e4a2-107">O primeiro é entender os algoritmos expressados por uma árvore de expressão para que ela possa ser movida para outro ambiente.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="8e4a2-108">O segundo é quando você deseja alterar o algoritmo que foi criado.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="8e4a2-109">Isso poderia ser feito para adicionar registro em log, interceptar chamadas de método e monitorá-las ou outras finalidades.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="8e4a2-110">Mover é visitar</span><span class="sxs-lookup"><span data-stu-id="8e4a2-110">Translating is Visiting</span></span>

<span data-ttu-id="8e4a2-111">O código que você compila para mover uma árvore de expressão é uma extensão do que você já viu para visitar todos os nós em uma árvore.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="8e4a2-112">Quando você move uma árvore de expressão, visita todos os nós e ao visitá-los, cria a nova árvore.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="8e4a2-113">A nova árvore pode conter referências aos nós originais ou aos novos nós que você colocou na árvore.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="8e4a2-114">Vamos ver isso em ação, visitando uma árvore de expressão e criando uma nova árvore com alguns nós de substituição.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="8e4a2-115">Neste exemplo, vamos substituir qualquer constante com uma constante que seja dez vezes maior.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="8e4a2-116">Caso contrário, vamos deixar a árvore de expressão intacta.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="8e4a2-117">Em vez de ler o valor da constante e substituí-la por uma nova constante, faremos essa substituição através da troca do nó constante por um novo nó que executa a multiplicação.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="8e4a2-118">Aqui, quando você encontrar um nó constante, você criará um novo nó de multiplicação cujos filhos serão a constante original e a constante `10`:</span><span class="sxs-lookup"><span data-stu-id="8e4a2-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

<span data-ttu-id="8e4a2-119">Ao substituir o nó original pelo substituto, uma nova árvore será formada, contendo as nossas modificações.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="8e4a2-120">Podemos verificar isso compilando e executando a árvore substituída.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-120">We can verify that by compiling and executing the replaced tree.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

<span data-ttu-id="8e4a2-121">A criação de uma nova árvore é uma combinação da visita aos nós da árvore existentes e a criação de novos nós, inserindo-os na árvore.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="8e4a2-122">Este exemplo mostra a importância das árvores de expressão serem imutáveis.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="8e4a2-123">Observe que a nova árvore criada acima contém uma mistura de nós recém-criados e nós da árvore existente.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="8e4a2-124">E isso é seguro, porque os nós da árvore existente não podem ser modificados.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="8e4a2-125">Isso pode resultar em eficiências significativas de memória.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="8e4a2-126">Os mesmos nós podem ser usados em toda a árvore ou em várias árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="8e4a2-127">Como os nós não podem ser modificados, o mesmo nó pode ser reutilizado sempre que necessário.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="8e4a2-128">Percorrer e executar uma adição</span><span class="sxs-lookup"><span data-stu-id="8e4a2-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="8e4a2-129">Vamos verificar isso criando um segundo visitante que percorre a árvore de nós de adição e calcula o resultado.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="8e4a2-130">Você pode fazer isso com algumas modificações no visitante que utilizamos até agora.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-130">You can do this by making a couple modifications to the vistor that you've seen so far.</span></span> <span data-ttu-id="8e4a2-131">Nessa nova versão, o visitante retornará a soma parcial da operação de adição até este ponto.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="8e4a2-132">Para uma expressão constante, esse é simplesmente o valor da expressão constante.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="8e4a2-133">Para uma expressão de adição, o resultado será a soma dos operandos esquerdos e direitos, uma vez que essas árvores forem percorridas.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it 
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

<span data-ttu-id="8e4a2-134">Tem bastante código nisso, mas os conceitos são bastante acessíveis.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="8e4a2-135">Esse código visita filhos em uma pesquisa de profundidade inicial.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="8e4a2-136">Ao encontrar um nó constante, o visitante retorna o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="8e4a2-137">Depois de visitar ambos os filhos, os visitantes terão a soma que foi calculada para essa subárvore.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="8e4a2-138">Agora o nó de adição poderá computar sua soma.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="8e4a2-139">Uma vez que todos os nós da árvore de expressão forem visitados, a soma será calculada.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="8e4a2-140">Você pode executar o exemplo no depurador e rastrear a execução.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="8e4a2-141">Vamos facilitar o rastreamento de como os nós são analisados e como a soma é calculada, percorrendo a árvore.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by travsersing the tree.</span></span> <span data-ttu-id="8e4a2-142">Esta é uma versão atualizada do método de agregação que inclui bastante informação de rastreamento:</span><span class="sxs-lookup"><span data-stu-id="8e4a2-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

<span data-ttu-id="8e4a2-143">Executá-lo na mesma expressão produz o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="8e4a2-143">Running it on the same expression yields the following output:</span></span>

```
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

<span data-ttu-id="8e4a2-144">Rastreie a saída e acompanhe no código acima.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="8e4a2-145">Você será capaz de entender como o código visita cada nó e calcula a soma, à medida que percorre a árvore e localiza a soma.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="8e4a2-146">Agora, vejamos uma execução diferente, com a expressão fornecida por `sum1`:</span><span class="sxs-lookup"><span data-stu-id="8e4a2-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="8e4a2-147">Aqui está a saída ao examinar essa expressão:</span><span class="sxs-lookup"><span data-stu-id="8e4a2-147">Here's the output from examining this expression:</span></span>

```
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

<span data-ttu-id="8e4a2-148">Embora a resposta final seja a mesma, a forma de percorrer a árvore é completamente diferente.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="8e4a2-149">Os nós são percorridos em uma ordem diferente, porque a árvore foi construída com operações diferentes que ocorrem primeiro.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="8e4a2-150">Aprendendo mais</span><span class="sxs-lookup"><span data-stu-id="8e4a2-150">Learning More</span></span>

<span data-ttu-id="8e4a2-151">Este exemplo mostra um pequeno subconjunto do código que você compilaria para percorrer e interpretar os algoritmos representados por uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="8e4a2-152">Para obter uma discussão completa a respeito de todo o trabalho necessário para compilar uma biblioteca de finalidade geral que move árvores de expressão para outra linguagem, leia [esta série](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) escrita por Matt Warren.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="8e4a2-153">Ele entra em detalhes de como mover qualquer código que você pode encontrar em uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="8e4a2-154">Espero que você tenha visto o verdadeiro poder das árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="8e4a2-155">Você pode examinar um conjunto de códigos, fazer as alterações que desejar nesse código e executar a versão modificada.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="8e4a2-156">Como as árvores de expressão são imutáveis, você pode criar novas árvores usando os componentes de árvores existentes.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="8e4a2-157">Isso minimiza a quantidade de memória necessária para criar árvores de expressão modificadas.</span><span class="sxs-lookup"><span data-stu-id="8e4a2-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="8e4a2-158">Próximo – Resumindo</span><span class="sxs-lookup"><span data-stu-id="8e4a2-158">Next -- Summing up</span></span>](expression-trees-summary.md)
