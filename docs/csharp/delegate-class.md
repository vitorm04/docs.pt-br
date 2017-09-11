---
title: "System.Delegate e a palavra-chave “delegado”"
description: "Aprenda sobre as classes do .NET Framework que dão suporte a delegados e como eles são mapeados para a palavra-chave “delegado”."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 465326fe520d6a062609e0c4c471135ef88b0dd6
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="eb56b-104">System.Delegate e a palavra-chave `delegate`</span><span class="sxs-lookup"><span data-stu-id="eb56b-104">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="eb56b-105">Anterior</span><span class="sxs-lookup"><span data-stu-id="eb56b-105">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="eb56b-106">Este artigo abordará as classes do .NET Framework que dão suporte a delegados e como eles são mapeados para a palavra-chave `delegate`.</span><span class="sxs-lookup"><span data-stu-id="eb56b-106">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="eb56b-107">Definindo os tipos de delegado</span><span class="sxs-lookup"><span data-stu-id="eb56b-107">Defining Delegate Types</span></span>

<span data-ttu-id="eb56b-108">Vamos começar com a palavra-chave ‘delegate’, pois ela é basicamente o que você usará ao trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="eb56b-108">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="eb56b-109">O código que o compilador gera quando você usa a palavra-chave `delegate` será mapeado para chamadas de método que invocam membros das classes @System.Delegate e @System.MulticastDelegate.</span><span class="sxs-lookup"><span data-stu-id="eb56b-109">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the @System.Delegate and @System.MulticastDelegate classes.</span></span> 

<span data-ttu-id="eb56b-110">Você define um tipo de delegado usando uma sintaxe semelhante à definição de uma assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="eb56b-110">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="eb56b-111">Basta adicionar a palavra-chave `delegate` à definição.</span><span class="sxs-lookup"><span data-stu-id="eb56b-111">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="eb56b-112">Vamos continuar a usar o método List.Sort() como nosso exemplo.</span><span class="sxs-lookup"><span data-stu-id="eb56b-112">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="eb56b-113">A primeira etapa é criar um tipo para o delegado de comparação:</span><span class="sxs-lookup"><span data-stu-id="eb56b-113">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="eb56b-114">O compilador gera uma classe, derivada de `System.Delegate`, que corresponde à assinatura usada (nesse caso, um método que retorna um inteiro e tem dois argumentos).</span><span class="sxs-lookup"><span data-stu-id="eb56b-114">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="eb56b-115">O tipo do delegado é `Comparison`.</span><span class="sxs-lookup"><span data-stu-id="eb56b-115">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="eb56b-116">O tipo delegado `Comparison` é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="eb56b-116">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="eb56b-117">Para obter detalhes sobre os genéricos, consulte [aqui](generics.md).</span><span class="sxs-lookup"><span data-stu-id="eb56b-117">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="eb56b-118">Observe que a sintaxe pode aparecer como se estivesse declarando uma variável, mas na verdade está declarando um *tipo*.</span><span class="sxs-lookup"><span data-stu-id="eb56b-118">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="eb56b-119">Você pode definir tipos de delegado dentro de classes, diretamente dentro de namespaces ou até mesmo no namespace global.</span><span class="sxs-lookup"><span data-stu-id="eb56b-119">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="eb56b-120">Declarar tipos de delegado (ou outros tipos) diretamente no namespace global não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-120">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="eb56b-121">O compilador também gera manipuladores de adição e remoção para esse novo tipo de forma que os clientes dessa classe podem adicionar e remover métodos de uma lista de invocação de instância.</span><span class="sxs-lookup"><span data-stu-id="eb56b-121">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="eb56b-122">O compilador imporá que a assinatura do método que está sendo adicionado ou removido corresponda à assinatura usada ao declarar o método.</span><span class="sxs-lookup"><span data-stu-id="eb56b-122">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="eb56b-123">Declarando instâncias de delegados</span><span class="sxs-lookup"><span data-stu-id="eb56b-123">Declaring instances of delegates</span></span>

<span data-ttu-id="eb56b-124">Depois de definir o delegado, você pode criar uma instância desse tipo.</span><span class="sxs-lookup"><span data-stu-id="eb56b-124">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="eb56b-125">Como todas as variáveis em C#, você não pode declarar instâncias de delegado diretamente em um namespace ou no namespace global.</span><span class="sxs-lookup"><span data-stu-id="eb56b-125">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="eb56b-126">O tipo da variável é `Comparison<T>`, o tipo de delegado definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="eb56b-126">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="eb56b-127">O nome da variável é `comparator`.</span><span class="sxs-lookup"><span data-stu-id="eb56b-127">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="eb56b-128">Esse trecho de código acima declarou uma variável de membro dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="eb56b-128">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="eb56b-129">Você também pode declarar variáveis de delegado que são variáveis locais ou argumentos para métodos.</span><span class="sxs-lookup"><span data-stu-id="eb56b-129">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="eb56b-130">Invocando delegados</span><span class="sxs-lookup"><span data-stu-id="eb56b-130">Invoking Delegates</span></span>

<span data-ttu-id="eb56b-131">Você invoca os métodos que estão na lista de invocação de um delegado chamando esse delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-131">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="eb56b-132">Dentro do método `Sort()`, o código chamará o método de comparação para determinar em qual ordem posicionar objetos:</span><span class="sxs-lookup"><span data-stu-id="eb56b-132">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="eb56b-133">Na linha acima, o código *invoca* o método anexado ao delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-133">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="eb56b-134">Você trata a variável como um nome de método e a invoca usando a sintaxe de chamada de método normal.</span><span class="sxs-lookup"><span data-stu-id="eb56b-134">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="eb56b-135">Essa linha de código faz uma suposição não segura: não há garantia de que um destino foi adicionado ao delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-135">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="eb56b-136">Se nenhum destino tiver sido anexado, a linha acima fará com que um `NullReferenceException` seja lançado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-136">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="eb56b-137">As expressões usadas para resolver esse problema são mais complicadas do que uma simples verificação de null e são abordadas posteriormente nesta [série](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="eb56b-137">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="eb56b-138">Atribuindo, adicionando e remondo destinos de invocação</span><span class="sxs-lookup"><span data-stu-id="eb56b-138">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="eb56b-139">Essa é a forma como o tipo do delegado é definido e como as instâncias de delegado são declaradas e invocadas.</span><span class="sxs-lookup"><span data-stu-id="eb56b-139">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="eb56b-140">Os desenvolvedores que desejam usar o método `List.Sort()` precisa definir um método cuja assinatura corresponde à definição de tipo de delegado e atribuí-lo ao delegado usado pelo método de classificação.</span><span class="sxs-lookup"><span data-stu-id="eb56b-140">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="eb56b-141">Esta atribuição adiciona o método à lista de invocação do objeto de delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-141">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="eb56b-142">Suponha que você queira classificar uma lista de cadeias de caracteres pelo seu comprimento.</span><span class="sxs-lookup"><span data-stu-id="eb56b-142">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="eb56b-143">A função de comparação pode ser a seguinte:</span><span class="sxs-lookup"><span data-stu-id="eb56b-143">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right)
{
    return left.Length.CompareTo(right.Length);
}
```

<span data-ttu-id="eb56b-144">O método é declarado como um método particular.</span><span class="sxs-lookup"><span data-stu-id="eb56b-144">The method is declared as a private method.</span></span> <span data-ttu-id="eb56b-145">Tudo bem.</span><span class="sxs-lookup"><span data-stu-id="eb56b-145">That's fine.</span></span> <span data-ttu-id="eb56b-146">Você pode não desejar que esse método seja parte da sua interface pública.</span><span class="sxs-lookup"><span data-stu-id="eb56b-146">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="eb56b-147">Ele ainda pode ser usado como o método de comparação ao anexar a um delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-147">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="eb56b-148">O código de chamada terá esse método anexado à lista de destino do objeto de delegado e pode acessá-lo por meio do delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-148">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="eb56b-149">Você cria essa relação passando esse método para o método `List.Sort()`:</span><span class="sxs-lookup"><span data-stu-id="eb56b-149">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="eb56b-150">Observe que o nome do método é usado, sem parênteses.</span><span class="sxs-lookup"><span data-stu-id="eb56b-150">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="eb56b-151">Usar o método como um argumento informa ao compilador para converter a referência de método em uma referência que pode ser usada como um destino de invocação do delegado e anexar esse método como um destino de invocação.</span><span class="sxs-lookup"><span data-stu-id="eb56b-151">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="eb56b-152">Você também poderia ter sido explícito declarando uma variável do tipo 'Comparison<string>' e fazendo uma atribuição:</span><span class="sxs-lookup"><span data-stu-id="eb56b-152">You could also have been explicit by declaring a variable of type 'Comparison<string>\` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="eb56b-153">Em usos em que o método que está sendo usado como um destino de delegado é um método pequeno, é comum usar a sintaxe da [Expressão Lambda](lambda-expressions.md) para executar a atribuição:</span><span class="sxs-lookup"><span data-stu-id="eb56b-153">In uses where the method being used as a delegate target is a small method, it's common to use [Lambda Expression](lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="eb56b-154">O uso de Expressões Lambda para destinos de delegado é mais abordado em uma [seção posterior](delegates-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="eb56b-154">Using Lambda Expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="eb56b-155">O exemplo de Sort() normalmente anexa um único método de destino ao delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-155">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="eb56b-156">No entanto, objetos delegados dão suporte a listas de invocação que têm vários métodos de destino anexados a um objeto de delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-156">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="eb56b-157">Classes Delegate e MulticastDelegate</span><span class="sxs-lookup"><span data-stu-id="eb56b-157">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="eb56b-158">O suporte de linguagem descrito acima fornece os recursos e o suporte que você normalmente precisará para trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="eb56b-158">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="eb56b-159">Esses recursos são criados em duas classes no .NET Core Framework: @System.Delegate e @"System.MulticastDelegate".</span><span class="sxs-lookup"><span data-stu-id="eb56b-159">These features are built on two classes in the .NET Core framework: @System.Delegate and @"System.MulticastDelegate".</span></span>

<span data-ttu-id="eb56b-160">A classe `System.Delegate` e sua única subclasse direta, `System.MulticastDelegate`, fornecem o suporte de estrutura para criar delegados, registrar métodos como destinos de delegado e invocar todos os métodos que são registrados como um destino de delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-160">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="eb56b-161">Curiosamente, as classes `System.Delegate` e `System.MulticastDelegate` não são em si tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-161">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="eb56b-162">Elas fornecem a base para todos os tipos de delegado específicos.</span><span class="sxs-lookup"><span data-stu-id="eb56b-162">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="eb56b-163">Esse mesmo processo de design de linguagem determinou que você não pode declarar uma classe que deriva de `Delegate` ou `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="eb56b-163">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="eb56b-164">As regras da linguagem C# proíbem isso.</span><span class="sxs-lookup"><span data-stu-id="eb56b-164">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="eb56b-165">Em vez disso, o compilador C# cria instâncias de uma classe derivada de `MulticastDelegate` quando você usa a palavra-chave da linguagem C# para declarar os tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-165">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="eb56b-166">Esse design tem suas raízes na primeira versão do C# e do .NET.</span><span class="sxs-lookup"><span data-stu-id="eb56b-166">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="eb56b-167">Uma meta da equipe de design era garantir que a linguagem aplicava a segurança de tipos ao usar delegados.</span><span class="sxs-lookup"><span data-stu-id="eb56b-167">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="eb56b-168">Isso significava garantir que os delegados fossem invocados com o tipo e o número de argumentos certos.</span><span class="sxs-lookup"><span data-stu-id="eb56b-168">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="eb56b-169">E, que algum tipo de retorno fosse indicado no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="eb56b-169">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="eb56b-170">Os delegados faziam parte da versão 1.0 do .NET, que era anterior aos genéricos.</span><span class="sxs-lookup"><span data-stu-id="eb56b-170">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="eb56b-171">A melhor maneira de reforçar essa segurança de tipos foi o compilador criar as classes de delegado concretas que representavam a assinatura do método sendo usado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-171">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="eb56b-172">Embora não seja possível criar classes derivadas diretamente, você usará os métodos definidos nessas classes.</span><span class="sxs-lookup"><span data-stu-id="eb56b-172">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="eb56b-173">Vamos percorrer os métodos mais comuns que você usará ao trabalhar com delegados.</span><span class="sxs-lookup"><span data-stu-id="eb56b-173">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="eb56b-174">O primeiro e mais importante fato a se lembrar é que todos os delegados com os quais você trabalha são derivados de `MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="eb56b-174">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="eb56b-175">Um delegado multicast significa que mais de um destino de método pode ser invocado durante a invocação através de um delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-175">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="eb56b-176">O design original considerava fazer uma distinção entre delegados em que somente um método de destino poderia ser anexado e invocado e delegados em que vários métodos de destino poderiam ser anexados e invocados.</span><span class="sxs-lookup"><span data-stu-id="eb56b-176">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="eb56b-177">Essa distinção provou ser menos útil na prática do que pensado originalmente.</span><span class="sxs-lookup"><span data-stu-id="eb56b-177">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="eb56b-178">As duas classes diferentes já foram criadas e estão na estrutura desde seu lançamento público inicial.</span><span class="sxs-lookup"><span data-stu-id="eb56b-178">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="eb56b-179">Os métodos que você usará mais com delegados são `Invoke()` e `BeginInvoke()` / `EndInvoke()`.</span><span class="sxs-lookup"><span data-stu-id="eb56b-179">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="eb56b-180">`Invoke()` invocará todos os métodos que foram anexados a uma instância de delegado específica.</span><span class="sxs-lookup"><span data-stu-id="eb56b-180">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="eb56b-181">Como você viu anteriormente, normalmente invoca delegados usando a sintaxe de chamada de método na variável de delegado.</span><span class="sxs-lookup"><span data-stu-id="eb56b-181">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="eb56b-182">Como você verá [posteriormente nesta série](delegates-patterns.md), existem padrões que trabalham diretamente com esses métodos.</span><span class="sxs-lookup"><span data-stu-id="eb56b-182">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="eb56b-183">Agora que você viu a sintaxe da linguagem e as classes que dão suporte a delegados, vamos examinar como os delegados fortemente tipados são usados, criados e invocados.</span><span class="sxs-lookup"><span data-stu-id="eb56b-183">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="eb56b-184">Avançar</span><span class="sxs-lookup"><span data-stu-id="eb56b-184">Next</span></span>](delegates-strongly-typed.md)

