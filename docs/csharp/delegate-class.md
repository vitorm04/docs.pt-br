---
title: System.Delegate e a palavra-chave `delegate`
description: Aprenda sobre as classes do .NET Framework que dão suporte a delegados e como eles são mapeados para a palavra-chave “delegado”.
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 4cf2b113fc9e2c6621f648af7ecb272a42b1f056
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465770"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="2b291-103">System.Delegate e a palavra-chave `delegate`</span><span class="sxs-lookup"><span data-stu-id="2b291-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="2b291-104">Anterior</span><span class="sxs-lookup"><span data-stu-id="2b291-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="2b291-105">Este artigo abordará as classes do .NET Framework que dão suporte a delegados e como eles são mapeados para a palavra-chave `delegate`.</span><span class="sxs-lookup"><span data-stu-id="2b291-105">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="2b291-106">Definindo os tipos de delegado</span><span class="sxs-lookup"><span data-stu-id="2b291-106">Defining Delegate Types</span></span>

<span data-ttu-id="2b291-107">Vamos começar com a palavra-chave ‘delegate’, pois ela é basicamente o que você usará ao trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="2b291-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="2b291-108">O código que o compilador gera quando você usa a palavra-chave `delegate` será mapeado para chamadas de método que invocam membros das classes <xref:System.Delegate> e <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="2b291-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="2b291-109">Você define um tipo de delegado usando uma sintaxe semelhante à definição de uma assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="2b291-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="2b291-110">Basta adicionar a palavra-chave `delegate` à definição.</span><span class="sxs-lookup"><span data-stu-id="2b291-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="2b291-111">Vamos continuar a usar o método List.Sort() como nosso exemplo.</span><span class="sxs-lookup"><span data-stu-id="2b291-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="2b291-112">A primeira etapa é criar um tipo para o delegado de comparação:</span><span class="sxs-lookup"><span data-stu-id="2b291-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="2b291-113">O compilador gera uma classe, derivada de `System.Delegate`, que corresponde à assinatura usada (nesse caso, um método que retorna um inteiro e tem dois argumentos).</span><span class="sxs-lookup"><span data-stu-id="2b291-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="2b291-114">O tipo do delegado é `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="2b291-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="2b291-115">O tipo delegado `Comparison` é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="2b291-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="2b291-116">Para obter detalhes sobre os genéricos, consulte [aqui](generics.md).</span><span class="sxs-lookup"><span data-stu-id="2b291-116">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="2b291-117">Observe que a sintaxe pode aparecer como se estivesse declarando uma variável, mas na verdade está declarando um *tipo*.</span><span class="sxs-lookup"><span data-stu-id="2b291-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="2b291-118">Você pode definir tipos de delegado dentro de classes, diretamente dentro de namespaces ou até mesmo no namespace global.</span><span class="sxs-lookup"><span data-stu-id="2b291-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="2b291-119">Declarar tipos de delegado (ou outros tipos) diretamente no namespace global não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="2b291-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="2b291-120">O compilador também gera manipuladores de adição e remoção para esse novo tipo de forma que os clientes dessa classe podem adicionar e remover métodos de uma lista de invocação de instância.</span><span class="sxs-lookup"><span data-stu-id="2b291-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="2b291-121">O compilador imporá que a assinatura do método que está sendo adicionado ou removido corresponda à assinatura usada ao declarar o método.</span><span class="sxs-lookup"><span data-stu-id="2b291-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="2b291-122">Declarando instâncias de delegados</span><span class="sxs-lookup"><span data-stu-id="2b291-122">Declaring instances of delegates</span></span>

<span data-ttu-id="2b291-123">Depois de definir o delegado, você pode criar uma instância desse tipo.</span><span class="sxs-lookup"><span data-stu-id="2b291-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="2b291-124">Como todas as variáveis em C#, você não pode declarar instâncias de delegado diretamente em um namespace ou no namespace global.</span><span class="sxs-lookup"><span data-stu-id="2b291-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="2b291-125">O tipo da variável é `Comparison<T>`, o tipo de delegado definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2b291-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="2b291-126">O nome da variável é `comparator`.</span><span class="sxs-lookup"><span data-stu-id="2b291-126">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="2b291-127">Esse snippet de código acima declarou uma variável de membro dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="2b291-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="2b291-128">Você também pode declarar variáveis de delegado que são variáveis locais ou argumentos para métodos.</span><span class="sxs-lookup"><span data-stu-id="2b291-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="2b291-129">Invocando delegados</span><span class="sxs-lookup"><span data-stu-id="2b291-129">Invoking Delegates</span></span>

<span data-ttu-id="2b291-130">Você invoca os métodos que estão na lista de invocação de um delegado chamando esse delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="2b291-131">Dentro do método `Sort()`, o código chamará o método de comparação para determinar em qual ordem posicionar objetos:</span><span class="sxs-lookup"><span data-stu-id="2b291-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="2b291-132">Na linha acima, o código *invoca* o método anexado ao delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="2b291-133">Você trata a variável como um nome de método e a invoca usando a sintaxe de chamada de método normal.</span><span class="sxs-lookup"><span data-stu-id="2b291-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="2b291-134">Essa linha de código faz uma suposição não segura: Não há nenhuma garantia de que um destino foi adicionado ao delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="2b291-135">Se nenhum destino tiver sido anexado, a linha acima fará com que um `NullReferenceException` seja lançado.</span><span class="sxs-lookup"><span data-stu-id="2b291-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="2b291-136">As expressões usadas para resolver esse problema são mais complicadas do que uma simples verificação de null e são abordadas posteriormente nesta [série](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="2b291-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="2b291-137">Atribuindo, adicionando e remondo destinos de invocação</span><span class="sxs-lookup"><span data-stu-id="2b291-137">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="2b291-138">Essa é a forma como o tipo do delegado é definido e como as instâncias de delegado são declaradas e invocadas.</span><span class="sxs-lookup"><span data-stu-id="2b291-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="2b291-139">Os desenvolvedores que desejam usar o método `List.Sort()` precisa definir um método cuja assinatura corresponde à definição de tipo de delegado e atribuí-lo ao delegado usado pelo método de classificação.</span><span class="sxs-lookup"><span data-stu-id="2b291-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="2b291-140">Esta atribuição adiciona o método à lista de invocação do objeto de delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="2b291-141">Suponha que você queira classificar uma lista de cadeias de caracteres pelo seu comprimento.</span><span class="sxs-lookup"><span data-stu-id="2b291-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="2b291-142">A função de comparação pode ser a seguinte:</span><span class="sxs-lookup"><span data-stu-id="2b291-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="2b291-143">O método é declarado como um método particular.</span><span class="sxs-lookup"><span data-stu-id="2b291-143">The method is declared as a private method.</span></span> <span data-ttu-id="2b291-144">Tudo bem.</span><span class="sxs-lookup"><span data-stu-id="2b291-144">That's fine.</span></span> <span data-ttu-id="2b291-145">Você pode não desejar que esse método seja parte da sua interface pública.</span><span class="sxs-lookup"><span data-stu-id="2b291-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="2b291-146">Ele ainda pode ser usado como o método de comparação ao anexar a um delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="2b291-147">O código de chamada terá esse método anexado à lista de destino do objeto de delegado e pode acessá-lo por meio do delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="2b291-148">Você cria essa relação passando esse método para o método `List.Sort()`:</span><span class="sxs-lookup"><span data-stu-id="2b291-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="2b291-149">Observe que o nome do método é usado, sem parênteses.</span><span class="sxs-lookup"><span data-stu-id="2b291-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="2b291-150">Usar o método como um argumento informa ao compilador para converter a referência de método em uma referência que pode ser usada como um destino de invocação do delegado e anexar esse método como um destino de invocação.</span><span class="sxs-lookup"><span data-stu-id="2b291-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="2b291-151">Você também poderia ter sido explícito declarando uma variável do tipo `Comparison<string>` e fazendo uma atribuição:</span><span class="sxs-lookup"><span data-stu-id="2b291-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="2b291-152">Em utilizações em que o método que está sendo usado como um destinos de delegado é um método pequeno, é comum usar a sintaxe da [expressão lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) para executar a atribuição:</span><span class="sxs-lookup"><span data-stu-id="2b291-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="2b291-153">O uso de expressões lambda para destinos de delegado será abordado em uma [seção posterior](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="2b291-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="2b291-154">O exemplo de Sort() normalmente anexa um único método de destino ao delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="2b291-155">No entanto, objetos delegados dão suporte a listas de invocação que têm vários métodos de destino anexados a um objeto de delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="2b291-156">Classes Delegate e MulticastDelegate</span><span class="sxs-lookup"><span data-stu-id="2b291-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="2b291-157">O suporte de linguagem descrito acima fornece os recursos e o suporte que você normalmente precisará para trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="2b291-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="2b291-158">Esses recursos são criados com base em duas classes no .NET Core Framework: <xref:System.Delegate> e <xref:System.MulticastDelegate>.</span><span class="sxs-lookup"><span data-stu-id="2b291-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="2b291-159">A classe `System.Delegate` e sua única subclasse direta, `System.MulticastDelegate`, fornecem o suporte de estrutura para criar delegados, registrar métodos como destinos de delegado e invocar todos os métodos que são registrados como um destino de delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-159">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="2b291-160">Curiosamente, as classes `System.Delegate` e `System.MulticastDelegate` não são em si tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="2b291-161">Elas fornecem a base para todos os tipos de delegado específicos.</span><span class="sxs-lookup"><span data-stu-id="2b291-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="2b291-162">Esse mesmo processo de design de linguagem determinou que você não pode declarar uma classe que deriva de `Delegate` ou `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="2b291-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="2b291-163">As regras da linguagem C# proíbem isso.</span><span class="sxs-lookup"><span data-stu-id="2b291-163">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="2b291-164">Em vez disso, o compilador C# cria instâncias de uma classe derivada de `MulticastDelegate` quando você usa a palavra-chave da linguagem C# para declarar os tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="2b291-165">Esse design tem suas raízes na primeira versão do C# e do .NET.</span><span class="sxs-lookup"><span data-stu-id="2b291-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="2b291-166">Uma meta da equipe de design era garantir que a linguagem aplicava a segurança de tipos ao usar delegados.</span><span class="sxs-lookup"><span data-stu-id="2b291-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="2b291-167">Isso significava garantir que os delegados fossem invocados com o tipo e o número de argumentos certos.</span><span class="sxs-lookup"><span data-stu-id="2b291-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="2b291-168">E, que algum tipo de retorno fosse indicado no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="2b291-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="2b291-169">Os delegados faziam parte da versão 1.0 do .NET, que era anterior aos genéricos.</span><span class="sxs-lookup"><span data-stu-id="2b291-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="2b291-170">A melhor maneira de reforçar essa segurança de tipos foi o compilador criar as classes de delegado concretas que representavam a assinatura do método sendo usado.</span><span class="sxs-lookup"><span data-stu-id="2b291-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="2b291-171">Embora não seja possível criar classes derivadas diretamente, você usará os métodos definidos nessas classes.</span><span class="sxs-lookup"><span data-stu-id="2b291-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="2b291-172">Vamos percorrer os métodos mais comuns que você usará ao trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="2b291-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="2b291-173">O primeiro e mais importante fato a se lembrar é que todos os delegados com os quais você trabalha são derivados de `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="2b291-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="2b291-174">Um delegado multicast significa que mais de um destino de método pode ser invocado durante a invocação através de um delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="2b291-175">O design original considerava fazer uma distinção entre delegados em que somente um método de destino poderia ser anexado e invocado e delegados em que vários métodos de destino poderiam ser anexados e invocados.</span><span class="sxs-lookup"><span data-stu-id="2b291-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="2b291-176">Essa distinção provou ser menos útil na prática do que pensado originalmente.</span><span class="sxs-lookup"><span data-stu-id="2b291-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="2b291-177">As duas classes diferentes já foram criadas e estão na estrutura desde seu lançamento público inicial.</span><span class="sxs-lookup"><span data-stu-id="2b291-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="2b291-178">Os métodos que você usará mais com delegados são `Invoke()` e `BeginInvoke()` / `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="2b291-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="2b291-179">`Invoke()` invocará todos os métodos que foram anexados a uma instância de delegado específica.</span><span class="sxs-lookup"><span data-stu-id="2b291-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="2b291-180">Como você viu anteriormente, normalmente invoca delegados usando a sintaxe de chamada de método na variável de delegado.</span><span class="sxs-lookup"><span data-stu-id="2b291-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="2b291-181">Como você verá [posteriormente nesta série](delegates-patterns.md), existem padrões que trabalham diretamente com esses métodos.</span><span class="sxs-lookup"><span data-stu-id="2b291-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="2b291-182">Agora que você viu a sintaxe da linguagem e as classes que dão suporte a delegados, vamos examinar como os delegados fortemente tipados são usados, criados e invocados.</span><span class="sxs-lookup"><span data-stu-id="2b291-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="2b291-183">Avançar</span><span class="sxs-lookup"><span data-stu-id="2b291-183">Next</span></span>](delegates-strongly-typed.md)
