---
title: Bugs misturados de código declarativo/código obrigatório (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 56d8140613f3dae7f99c1374634dbd8bdf094a7c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44192607"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="20dba-102">Bugs misturados de código declarativo/código obrigatório (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="20dba-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="20dba-103"> contém vários métodos que permitem que você modifique uma árvore XML diretamente.</span><span class="sxs-lookup"><span data-stu-id="20dba-103"> contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="20dba-104">Você pode adicionar elementos, excluir elementos, modifica o conteúdo de um elemento, adiciona atributos, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="20dba-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="20dba-105">Essa interface de programação é descrita em [Modificando árvores XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="20dba-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="20dba-106">Se você estiver iterando com um dos eixos, como <xref:System.Xml.Linq.XContainer.Elements%2A>, e você está alterando a árvore XML como você itera através do eixo, você pode acabar com alguns erros estranhas.</span><span class="sxs-lookup"><span data-stu-id="20dba-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="20dba-107">Esse problema é às vezes conhecido como “o problema do Dia De Bruxas”.</span><span class="sxs-lookup"><span data-stu-id="20dba-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="20dba-108">Definição do problema</span><span class="sxs-lookup"><span data-stu-id="20dba-108">Definition of the Problem</span></span>  
 <span data-ttu-id="20dba-109">Quando você escrever qualquer código usando LINQ que itera através de uma coleção, você estiver escrevendo código em um estilo declarativo.</span><span class="sxs-lookup"><span data-stu-id="20dba-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="20dba-110">É mais próximo a descrever *o que* você deseja, em vez de *como* deseja que isso seja feito.</span><span class="sxs-lookup"><span data-stu-id="20dba-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="20dba-111">Se você escreve o código que 1) obtém o primeiro elemento, 2) testá-la para alguma condição, 3) altera-a, e 4) coloque-a de novo na lista, então este código seria obrigatório.</span><span class="sxs-lookup"><span data-stu-id="20dba-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="20dba-112">Você está informando o computador *como* deseja que isso seja feito.</span><span class="sxs-lookup"><span data-stu-id="20dba-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="20dba-113">Misturar esses estilos de código na mesma operação é o que resulta em problemas.</span><span class="sxs-lookup"><span data-stu-id="20dba-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="20dba-114">Considere o seguinte:</span><span class="sxs-lookup"><span data-stu-id="20dba-114">Consider the following:</span></span>  
  
 <span data-ttu-id="20dba-115">Suponha que você tenha uma lista vinculada com três itens nele (a, b, e c#):</span><span class="sxs-lookup"><span data-stu-id="20dba-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="20dba-116">Agora, suponha que você deseja mover através da lista vinculada, adicionando novos itens três (a, b, e c#).</span><span class="sxs-lookup"><span data-stu-id="20dba-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="20dba-117">Você deseja a lista vinculada resultante para ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="20dba-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="20dba-118">Assim você escreve o código que itera através da lista, e para cada item, adicione um novo item mesmo após ele.</span><span class="sxs-lookup"><span data-stu-id="20dba-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="20dba-119">O que acontece são que seu código verá o primeiro elemento de `a` , e inserção `a'` após ele.</span><span class="sxs-lookup"><span data-stu-id="20dba-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="20dba-120">Agora, seu código se o nó seguir na lista, que agora é `a'`!</span><span class="sxs-lookup"><span data-stu-id="20dba-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="20dba-121">Felizmente adicionar um novo item à lista, `a''`.</span><span class="sxs-lookup"><span data-stu-id="20dba-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="20dba-122">Como você determinaria este no mundo real?</span><span class="sxs-lookup"><span data-stu-id="20dba-122">How would you solve this in the real world?</span></span> <span data-ttu-id="20dba-123">Bem, você pode fazer uma cópia do original associado para listar, e criar uma lista completamente nova.</span><span class="sxs-lookup"><span data-stu-id="20dba-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="20dba-124">Ou se você estiver escrevendo código puramente obrigatório, você pode localizar o primeiro item, adiciona o novo item, e então avanço duas vezes na lista vinculada, adiantando sobre o elemento que você adicionou.</span><span class="sxs-lookup"><span data-stu-id="20dba-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="20dba-125">Adicionar a iterar</span><span class="sxs-lookup"><span data-stu-id="20dba-125">Adding While Iterating</span></span>  
 <span data-ttu-id="20dba-126">Por exemplo, suponha que você deseja escrever qualquer código que para cada elemento em uma árvore, você deseja criar um elemento duplicado:</span><span class="sxs-lookup"><span data-stu-id="20dba-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="20dba-127">Esse código entra em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="20dba-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="20dba-128">A declaração de `foreach` itera através do eixo de `Elements()` , adicionando novos elementos para o elemento de `doc` .</span><span class="sxs-lookup"><span data-stu-id="20dba-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="20dba-129">Acaba também iterar através dos elementos que acabou de adicionar.</span><span class="sxs-lookup"><span data-stu-id="20dba-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="20dba-130">E como atribuir novos objetos com cada iteração do loop, consumirá se houver qualquer memória disponível.</span><span class="sxs-lookup"><span data-stu-id="20dba-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="20dba-131">Você pode corrigir este problema recebendo a coleção na memória usando o operador padrão de consulta de <xref:System.Linq.Enumerable.ToList%2A> , como segue:</span><span class="sxs-lookup"><span data-stu-id="20dba-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="20dba-132">Agora o código.</span><span class="sxs-lookup"><span data-stu-id="20dba-132">Now the code works.</span></span> <span data-ttu-id="20dba-133">A árvore XML resultante é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="20dba-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="20dba-134">Excluir para iterar</span><span class="sxs-lookup"><span data-stu-id="20dba-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="20dba-135">Se você deseja excluir todos os nós em um determinado nível, você pode ter tentado escrever código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="20dba-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="20dba-136">No entanto, isso não faz o que você deseja.</span><span class="sxs-lookup"><span data-stu-id="20dba-136">However, this does not do what you want.</span></span> <span data-ttu-id="20dba-137">Nesta situação, depois que você removesse o primeiro elemento, A, é removido da árvore XML contida na raiz, e o código no método dos elementos que está fazendo iterar não pode localizar o elemento seguir.</span><span class="sxs-lookup"><span data-stu-id="20dba-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="20dba-138">O código anterior gerencia a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="20dba-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="20dba-139">A solução é novamente chamar <xref:System.Linq.Enumerable.ToList%2A> para materializar a coleção, como segue:</span><span class="sxs-lookup"><span data-stu-id="20dba-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="20dba-140">Isso gerencia a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="20dba-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="20dba-141">Como alternativa, você pode eliminar a iteração completamente chamando <xref:System.Xml.Linq.XElement.RemoveAll%2A> no elemento pai:</span><span class="sxs-lookup"><span data-stu-id="20dba-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="20dba-142">Por que não pode automaticamente LINQ manipular esse?</span><span class="sxs-lookup"><span data-stu-id="20dba-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="20dba-143">Uma abordagem seria sempre trazer tudo na memória em vez de fazer a avaliação lazy.</span><span class="sxs-lookup"><span data-stu-id="20dba-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="20dba-144">No entanto, seria muito cara em termos de uso de desempenho e de memória.</span><span class="sxs-lookup"><span data-stu-id="20dba-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="20dba-145">De fato, se LINQ e LINQ to (XML) foi tomar essa abordagem, falharia em situações do mundo real.</span><span class="sxs-lookup"><span data-stu-id="20dba-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="20dba-146">Outra abordagem seria possível colocar o meio em alguma sintaxe de transação em LINQ, e tem a tentativa de compilador analisar o código e de determinar se as coleções específicas de precisa ser materializada.</span><span class="sxs-lookup"><span data-stu-id="20dba-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="20dba-147">No entanto, tentar determinar qualquer código que tiver efeitos colaterais é incredibly complexa.</span><span class="sxs-lookup"><span data-stu-id="20dba-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="20dba-148">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="20dba-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="20dba-149">Esse código de análise precisaria analisar métodos TestSomeCondition e DoMyProjection, e todos os métodos que esses métodos chamados a partir, para determinar se qualquer código tinha efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="20dba-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="20dba-150">Mas o código de análise não pode apenas procurar qualquer código que tem efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="20dba-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="20dba-151">Precisaria para selecionar apenas o código que tinha efeitos colaterais em elementos filho de `root` nesta situação.</span><span class="sxs-lookup"><span data-stu-id="20dba-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="20dba-152">LINQ to XML não tenta fazer uma análise.</span><span class="sxs-lookup"><span data-stu-id="20dba-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="20dba-153">Você pode para evitar esses problemas.</span><span class="sxs-lookup"><span data-stu-id="20dba-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="20dba-154">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="20dba-154">Guidance</span></span>  
 <span data-ttu-id="20dba-155">Primeiro, não mistura o código declarativo e obrigatório.</span><span class="sxs-lookup"><span data-stu-id="20dba-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="20dba-156">Mesmo se você souber exatamente a semântica das coleções e semântica dos métodos que modificam a árvore XML, se você escrever qualquer código inteligente que impede essas categorias de problemas, seu código deverá ser mantido no futuro por outros desenvolvedores, e não podem ser como o espaço livre nos problemas.</span><span class="sxs-lookup"><span data-stu-id="20dba-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="20dba-157">Se você mistura estilos declarativo e obrigatórias de codificação, seu código será mais frágil.</span><span class="sxs-lookup"><span data-stu-id="20dba-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="20dba-158">Se você escreve o código que materializa uma coleção para que esses problemas são impedidos, observar-la com comentários apropriadas em seu código, para que os desenvolvedores de aplicativos compreendam o problema.</span><span class="sxs-lookup"><span data-stu-id="20dba-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="20dba-159">Segundo, se o desempenho e outras considerações reservam, use somente o código declarativo.</span><span class="sxs-lookup"><span data-stu-id="20dba-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="20dba-160">Não altere sua árvore XML existente.</span><span class="sxs-lookup"><span data-stu-id="20dba-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="20dba-161">Gerencia um novo.</span><span class="sxs-lookup"><span data-stu-id="20dba-161">Generate a new one.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20dba-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20dba-162">See Also</span></span>

- [<span data-ttu-id="20dba-163">Programação LINQ to XML avançada (C#)</span><span class="sxs-lookup"><span data-stu-id="20dba-163">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
