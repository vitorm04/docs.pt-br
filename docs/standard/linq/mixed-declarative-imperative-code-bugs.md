---
title: Bugs de código declarativo/imperativo misto-LINQ to XML
description: Saiba como reconhecer e evitar problemas que podem ocorrer quando o código é iterado ao longo de um eixo que faz alterações.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 280bb62d15ff28d1fd09ca2d0c52c0a0c36d7282
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551963"
---
# <a name="mixed-declarativeimperative-code-bugs-linq-to-xml"></a><span data-ttu-id="e812c-103">Bugs de código declarativo/imperativo mistos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e812c-103">Mixed declarative/imperative code bugs (LINQ to XML)</span></span>

<span data-ttu-id="e812c-104">O LINQ to XML contém vários métodos que permitem que você modifique uma árvore XML diretamente.</span><span class="sxs-lookup"><span data-stu-id="e812c-104">LINQ to XML contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="e812c-105">Você pode adicionar elementos, excluir elementos, modifica o conteúdo de um elemento, adiciona atributos, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="e812c-105">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="e812c-106">Essa interface de programação é descrita em [Modificar árvores XML](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="e812c-106">This programming interface is described in [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span> <span data-ttu-id="e812c-107">Se você estiver Iterando por meio de um dos eixos, como <xref:System.Xml.Linq.XContainer.Elements%2A> e estiver modificando a árvore XML à medida que itera pelo eixo, poderá acabar com alguns bugs estranhos.</span><span class="sxs-lookup"><span data-stu-id="e812c-107">If you're iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you're modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>

<span data-ttu-id="e812c-108">Esse problema é às vezes conhecido como “o problema do Dia De Bruxas”.</span><span class="sxs-lookup"><span data-stu-id="e812c-108">This problem is sometimes known as "The Halloween Problem".</span></span>

<span data-ttu-id="e812c-109">Quando você escreve um código usando LINQ que itera em uma coleção, você está escrevendo código em um estilo declarativo.</span><span class="sxs-lookup"><span data-stu-id="e812c-109">When you write some code using LINQ that iterates through a collection, you're writing code in a declarative style.</span></span> <span data-ttu-id="e812c-110">É mais semelhante a descrever *o que* você deseja, em vez de *como* você deseja fazer isso.</span><span class="sxs-lookup"><span data-stu-id="e812c-110">It's more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="e812c-111">Se você escreve o código que 1) obtém o primeiro elemento, 2) testá-la para alguma condição, 3) altera-a, e 4) coloque-a de novo na lista, então este código seria obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e812c-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="e812c-112">Você está informando ao computador *como* fazer o que você deseja concluir.</span><span class="sxs-lookup"><span data-stu-id="e812c-112">You're telling the computer *how* to do what you want done.</span></span>

<span data-ttu-id="e812c-113">Misturar esses estilos de código na mesma operação é o que resulta em problemas.</span><span class="sxs-lookup"><span data-stu-id="e812c-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="e812c-114">Considere o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e812c-114">Consider the following:</span></span>

<span data-ttu-id="e812c-115">Suponha que você tenha uma lista vinculada com três itens nele (a, b, e c#):</span><span class="sxs-lookup"><span data-stu-id="e812c-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>

> <span data-ttu-id="e812c-116">a-> b-> c</span><span class="sxs-lookup"><span data-stu-id="e812c-116">a -> b -> c</span></span>

<span data-ttu-id="e812c-117">Agora, suponha que você deseja mover através da lista vinculada, adicionando novos itens três (a, b, e c#).</span><span class="sxs-lookup"><span data-stu-id="e812c-117">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="e812c-118">Você deseja a lista vinculada resultante para ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="e812c-118">You want the resulting linked list to look like this:</span></span>

 > <span data-ttu-id="e812c-119">a-> um '-> b-> b '-> c-> c '</span><span class="sxs-lookup"><span data-stu-id="e812c-119">a -> a' -> b -> b' -> c -> c'</span></span>

<span data-ttu-id="e812c-120">Assim você escreve o código que itera através da lista, e para cada item, adicione um novo item mesmo após ele.</span><span class="sxs-lookup"><span data-stu-id="e812c-120">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="e812c-121">O que acontece são que seu código verá o primeiro elemento de `a` , e inserção `a'` após ele.</span><span class="sxs-lookup"><span data-stu-id="e812c-121">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="e812c-122">Agora, seu código será movido para o próximo nó da lista, que agora é `a'` , portanto, adiciona um novo item entre um ' e o b à lista!</span><span class="sxs-lookup"><span data-stu-id="e812c-122">Now, your code will move to the next node in the list, which is now `a'`, so it adds a new item between a' and b to the list!</span></span>

<span data-ttu-id="e812c-123">Como você resolveria isso?</span><span class="sxs-lookup"><span data-stu-id="e812c-123">How would you solve this?</span></span> <span data-ttu-id="e812c-124">Bem, você pode fazer uma cópia do original associado para listar, e criar uma lista completamente nova.</span><span class="sxs-lookup"><span data-stu-id="e812c-124">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="e812c-125">Ou, se você estiver escrevendo código puramente imperativo, poderá encontrar o primeiro item, adicionar o novo item e, em seguida, avançar duas vezes na lista vinculada, avançando sobre o elemento que você acabou de adicionar.</span><span class="sxs-lookup"><span data-stu-id="e812c-125">Or if you're writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>

## <a name="example-adding-while-iterating"></a><span data-ttu-id="e812c-126">Exemplo: adicionando ao iterar</span><span class="sxs-lookup"><span data-stu-id="e812c-126">Example: Adding while iterating</span></span>

<span data-ttu-id="e812c-127">Por exemplo, suponha que você queira escrever código para criar uma duplicata de cada elemento em uma árvore:</span><span class="sxs-lookup"><span data-stu-id="e812c-127">For example, suppose you want to write code to create a duplicate of every element in a tree:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    root.Add(new XElement(e.Name, (string)e));
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    root.Add(New XElement(e.Name, e.Value))
Next
```

<span data-ttu-id="e812c-128">Esse código entra em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="e812c-128">This code goes into an infinite loop.</span></span> <span data-ttu-id="e812c-129">A declaração de `foreach` itera através do eixo de `Elements()` , adicionando novos elementos para o elemento de `doc` .</span><span class="sxs-lookup"><span data-stu-id="e812c-129">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="e812c-130">Acaba também iterar através dos elementos que acabou de adicionar.</span><span class="sxs-lookup"><span data-stu-id="e812c-130">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="e812c-131">E como atribuir novos objetos com cada iteração do loop, consumirá se houver qualquer memória disponível.</span><span class="sxs-lookup"><span data-stu-id="e812c-131">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>

<span data-ttu-id="e812c-132">Você pode corrigir este problema recebendo a coleção na memória usando o operador padrão de consulta de <xref:System.Linq.Enumerable.ToList%2A> , como segue:</span><span class="sxs-lookup"><span data-stu-id="e812c-132">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    root.Add(new XElement(e.Name, (string)e));
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    root.Add(New XElement(e.Name, e.Value))
Next
Console.WriteLine(root)
```

<span data-ttu-id="e812c-133">Agora o código.</span><span class="sxs-lookup"><span data-stu-id="e812c-133">Now the code works.</span></span> <span data-ttu-id="e812c-134">A árvore XML resultante é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="e812c-134">The resulting XML tree is the following:</span></span>

```xml
<Root>
  <A>1</A>
  <B>2</B>
  <C>3</C>
  <A>1</A>
  <B>2</B>
  <C>3</C>
</Root>
```

## <a name="example-deleting-while-iterating"></a><span data-ttu-id="e812c-135">Exemplo: excluindo durante a iteração</span><span class="sxs-lookup"><span data-stu-id="e812c-135">Example: Deleting while iterating</span></span>

<span data-ttu-id="e812c-136">Se você deseja excluir todos os nós em um determinado nível, você pode ter tentado escrever código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e812c-136">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    e.Remove()
Next
Console.WriteLine(root)
```

<span data-ttu-id="e812c-137">No entanto, isso não faz o que você deseja.</span><span class="sxs-lookup"><span data-stu-id="e812c-137">However, this doesn't do what you want.</span></span> <span data-ttu-id="e812c-138">Nessa situação, depois de remover o primeiro elemento, A, ele é removido da árvore XML contida na raiz e o código no método Elements que faz a iteração não pode localizar o próximo elemento.</span><span class="sxs-lookup"><span data-stu-id="e812c-138">In this situation, after you've removed the first element, A, it's removed from the XML tree contained in root, and the code in the Elements method that does the iterating can't find the next element.</span></span>

<span data-ttu-id="e812c-139">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e812c-139">This example produces the following output:</span></span>

```xml
<Root>
  <B>2</B>
  <C>3</C>
</Root>
```

<span data-ttu-id="e812c-140">A solução é novamente chamar <xref:System.Linq.Enumerable.ToList%2A> para materializar a coleção, como segue:</span><span class="sxs-lookup"><span data-stu-id="e812c-140">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    e.Remove()
Next
Console.WriteLine(root)
```

<span data-ttu-id="e812c-141">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e812c-141">This example produces the following output:</span></span>

```xml
<Root />
```

<span data-ttu-id="e812c-142">Como alternativa, você pode eliminar a iteração completamente chamando <xref:System.Xml.Linq.XElement.RemoveAll%2A> no elemento pai:</span><span class="sxs-lookup"><span data-stu-id="e812c-142">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
root.RemoveAll();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
root.RemoveAll()
Console.WriteLine(root)
```

## <a name="example-why-linq-cant-automatically-handle-these-issues"></a><span data-ttu-id="e812c-143">Exemplo: por que o LINQ não pode lidar com esses problemas automaticamente</span><span class="sxs-lookup"><span data-stu-id="e812c-143">Example: Why LINQ can't automatically handle these issues</span></span>

<span data-ttu-id="e812c-144">Uma abordagem seria sempre trazer tudo na memória em vez de fazer a avaliação lazy.</span><span class="sxs-lookup"><span data-stu-id="e812c-144">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="e812c-145">No entanto, seria muito cara em termos de uso de desempenho e de memória.</span><span class="sxs-lookup"><span data-stu-id="e812c-145">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="e812c-146">Na verdade, se o LINQ e o LINQ to XML, tomaram essa abordagem, ele falharia em situações do mundo real.</span><span class="sxs-lookup"><span data-stu-id="e812c-146">In fact, if LINQ, and LINQ to XML, were to take this approach, it would fail in real-world situations.</span></span>

<span data-ttu-id="e812c-147">Outra abordagem possível seria colocar algum tipo de sintaxe de transação no LINQ, e fazer com que o compilador tentasse analisar o código para determinar se alguma coleção específica precisava ser materializada.</span><span class="sxs-lookup"><span data-stu-id="e812c-147">Another possible approach would be to put some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code to determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="e812c-148">No entanto, tentar determinar qualquer código que tiver efeitos colaterais é incredibly complexa.</span><span class="sxs-lookup"><span data-stu-id="e812c-148">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="e812c-149">Considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e812c-149">Consider the following code:</span></span>

```csharp
var z =
    from e in root.Elements()
    where TestSomeCondition(e)
    select DoMyProjection(e);
```

```vb
Dim z = _
    From e In root.Elements() _
    Where (TestSomeCondition(e)) _
    Select DoMyProjection(e)
```

<span data-ttu-id="e812c-150">Esse código de análise precisaria analisar métodos TestSomeCondition e DoMyProjection, e todos os métodos que esses métodos chamados a partir, para determinar se qualquer código tinha efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="e812c-150">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="e812c-151">Mas o código de análise não pode apenas procurar qualquer código que tem efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="e812c-151">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="e812c-152">Precisaria para selecionar apenas o código que tinha efeitos colaterais em elementos filho de `root` nesta situação.</span><span class="sxs-lookup"><span data-stu-id="e812c-152">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>

<span data-ttu-id="e812c-153">LINQ to XML não tenta fazer nenhuma análise.</span><span class="sxs-lookup"><span data-stu-id="e812c-153">LINQ to XML doesn't attempt to do any such analysis.</span></span> <span data-ttu-id="e812c-154">Cabe a você evitar esses problemas.</span><span class="sxs-lookup"><span data-stu-id="e812c-154">It's up to you to avoid these problems.</span></span>

## <a name="example-use-declarative-code-to-generate-a-new-xml-tree-rather-than-modify-the-existing-tree"></a><span data-ttu-id="e812c-155">Exemplo: Use o código declarativo para gerar uma nova árvore XML em vez de modificar a árvore existente</span><span class="sxs-lookup"><span data-stu-id="e812c-155">Example: Use declarative code to generate a new XML tree rather than modify the existing tree</span></span>

<span data-ttu-id="e812c-156">Para evitar esses problemas, não misture códigos declarativos e imperativos, mesmo se você souber exatamente a semântica de suas coleções e a semântica dos métodos que modificam a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="e812c-156">To avoid such problems, don't mix declarative and imperative code, even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree.</span></span> <span data-ttu-id="e812c-157">Se você escrever um código que evite problemas, seu código precisará ser mantido por outros desenvolvedores no futuro, e eles podem não estar tão claros quanto aos problemas.</span><span class="sxs-lookup"><span data-stu-id="e812c-157">If you write code that avoids problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="e812c-158">Se você mistura estilos declarativo e obrigatórias de codificação, seu código será mais frágil.</span><span class="sxs-lookup"><span data-stu-id="e812c-158">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  <span data-ttu-id="e812c-159">Se você escreve o código que materializa uma coleção para que esses problemas são impedidos, observar-la com comentários apropriadas em seu código, para que os desenvolvedores de aplicativos compreendam o problema.</span><span class="sxs-lookup"><span data-stu-id="e812c-159">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>

<span data-ttu-id="e812c-160">Se o desempenho e outras considerações permitirem, use apenas o código declarativo.</span><span class="sxs-lookup"><span data-stu-id="e812c-160">If performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="e812c-161">Não altere sua árvore XML existente.</span><span class="sxs-lookup"><span data-stu-id="e812c-161">Don't modify your existing XML tree.</span></span> <span data-ttu-id="e812c-162">Em vez disso, gere um novo, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e812c-162">Instead, generate a new one as shown in the following example:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
XElement newRoot = new XElement("Root",
    root.Elements(),
    root.Elements()
);
Console.WriteLine(newRoot);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
Dim newRoot As XElement = New XElement("Root", _
    root.Elements(), root.Elements())
Console.WriteLine(newRoot)
```
