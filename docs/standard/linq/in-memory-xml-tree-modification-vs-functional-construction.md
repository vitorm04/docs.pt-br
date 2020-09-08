---
title: Modificação da árvore XML na memória versus construção funcional-LINQ to XML
description: Veja exemplos de duas abordagens diferentes para modificar árvores XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 71f76d12024bb07cf90df2299df14646ae271b47
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551869"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml"></a><span data-ttu-id="b1d92-103">Modificação da árvore XML na memória versus construção funcional (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b1d92-103">In-memory XML tree modification vs. functional construction (LINQ to XML)</span></span>

<span data-ttu-id="b1d92-104">Modificar uma árvore XML no local é uma abordagem tradicional para alterar a forma de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="b1d92-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="b1d92-105">Um aplicativo típico carrega um documento em um armazenamento de dados, como DOM ou LINQ to XML; usa uma interface de programação para inserir ou excluir nós ou alterar o conteúdo; e, em seguida, salva o XML em um arquivo ou o transmite por uma rede.</span><span class="sxs-lookup"><span data-stu-id="b1d92-105">A typical application loads a document into a data store such as DOM or LINQ to XML; uses a programming interface to insert or delete nodes, or change their content; and then saves the XML to a file or transmits it over a network.</span></span>

<span data-ttu-id="b1d92-106">LINQ to XML habilita outra abordagem útil em muitos cenários: *construção funcional*.</span><span class="sxs-lookup"><span data-stu-id="b1d92-106">LINQ to XML enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="b1d92-107">Deleites funcionais de compilação que modificam dados como um problema de transformação, em vez de como tratamento detalhada de um armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="b1d92-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="b1d92-108">Se você pode ter uma representação dos dados e a transformação com eficiência de um formulário para outro, o resultado é o mesmo como se você recebe um armazenamento de dados e o manipulou de alguma maneira para executar outra forma.</span><span class="sxs-lookup"><span data-stu-id="b1d92-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="b1d92-109">Uma chave para a abordagem de construção funcional é passar os resultados de consultas para os construtores <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b1d92-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>

<span data-ttu-id="b1d92-110">Em muitos casos, você pode escrever o código de transformação em uma fração do tempo que levaria para manipular o armazenamento de dados, e o código resultante é mais robusto e mais fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="b1d92-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and the resulting code is more robust and easier to maintain.</span></span> <span data-ttu-id="b1d92-111">Nesses casos, embora a abordagem de transformação possa levar mais poder de processamento, é uma maneira mais eficaz de modificar os dados.</span><span class="sxs-lookup"><span data-stu-id="b1d92-111">In these cases, even though the transformational approach can take more processing power, it's a more effective way to modify data.</span></span> <span data-ttu-id="b1d92-112">Se um desenvolvedor estiver familiarizado com a abordagem funcional, o código resultante em muitos casos será mais fácil de entender, e será fácil encontrar o código que modifica cada parte da árvore.</span><span class="sxs-lookup"><span data-stu-id="b1d92-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand, and it's easy to find the code that modifies each part of the tree.</span></span>

<span data-ttu-id="b1d92-113">A abordagem em que você modifica uma árvore XML em vigor é mais familiar para muitos programadores DOM, enquanto o código escrito usando a abordagem funcional pode parecer desconhecido para um desenvolvedor que ainda não entendeu essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="b1d92-113">The approach where you modify an XML tree in place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="b1d92-114">Se você precisa apenas fazer uma alteração pequena a uma grande árvore XML, a abordagem onde você altera uma árvore no lugar em muitos casos terá menos processador central - tempo.</span><span class="sxs-lookup"><span data-stu-id="b1d92-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>

<span data-ttu-id="b1d92-115">Este artigo fornece exemplos de ambas as abordagens.</span><span class="sxs-lookup"><span data-stu-id="b1d92-115">This article provides examples of both approaches.</span></span> <span data-ttu-id="b1d92-116">Suponha que você queira modificar o seguinte documento XML simples para que os atributos se tornem elementos:</span><span class="sxs-lookup"><span data-stu-id="b1d92-116">Suppose you want to modify the following simple XML document so that the attributes become elements:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root Data1="123" Data2="456">
  <Child1>Content</Child1>
</Root>
```

<span data-ttu-id="b1d92-117">O primeiro dos exemplos a seguir usa a abordagem de modificação in-loco tradicional, e a segunda usa a abordagem de construção funcional.</span><span class="sxs-lookup"><span data-stu-id="b1d92-117">The first of the following examples uses the traditional in-place modification approach, and the second uses the functional construction approach.</span></span>

## <a name="example-transform-attributes-into-elements-with-the-traditional-in-place-approach"></a><span data-ttu-id="b1d92-118">Exemplo: transformar atributos em elementos com a abordagem in-loco tradicional</span><span class="sxs-lookup"><span data-stu-id="b1d92-118">Example: Transform attributes into elements with the traditional in-place approach</span></span>

<span data-ttu-id="b1d92-119">Você pode escrever qualquer código procedural para criar elementos de atributos, e exclui os atributos, como segue:</span><span class="sxs-lookup"><span data-stu-id="b1d92-119">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
foreach (XAttribute att in root.Attributes()) {
    root.Add(new XElement(att.Name, (string)att));
}
root.Attributes().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
For Each att As XAttribute In root.Attributes()
    root.Add(New XElement(att.Name, att.Value))
Next
root.Attributes().Remove()
Console.WriteLine(root)
```

<span data-ttu-id="b1d92-120">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b1d92-120">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Content</Child1>
  <Data1>123</Data1>
  <Data2>456</Data2>
</Root>
```

## <a name="example-transform-attributes-into-elements-with-the-functional-construction-approach"></a><span data-ttu-id="b1d92-121">Exemplo: transformar atributos em elementos com a abordagem de construção funcional</span><span class="sxs-lookup"><span data-stu-id="b1d92-121">Example: Transform attributes into elements with the functional construction approach</span></span>

<span data-ttu-id="b1d92-122">Por outro lado, uma abordagem funcional consiste em código para formar uma nova árvore, selecionando e escolhendo elementos e atributos da árvore de origem e transformando-os conforme apropriado à medida que são adicionados à nova árvore.</span><span class="sxs-lookup"><span data-stu-id="b1d92-122">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they're added to the new tree.</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
XElement newTree = new XElement("Root",
    root.Element("Child1"),
    from att in root.Attributes()
    select new XElement(att.Name, (string)att)
);
Console.WriteLine(newTree);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim newTree As XElement = _
    <Root>
        <%= root.<Child1> %>
        <%= From att In root.Attributes() _
            Select New XElement(att.Name, att.Value) %>
    </Root>
Console.WriteLine(newTree)
```

<span data-ttu-id="b1d92-123">Saída deste exemplo mesmo XML que o primeiro exemplo.</span><span class="sxs-lookup"><span data-stu-id="b1d92-123">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="b1d92-124">No entanto, observe que você pode realmente consulte a estrutura XML resultante de novo na abordagem funcional.</span><span class="sxs-lookup"><span data-stu-id="b1d92-124">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="b1d92-125">Você pode ver a criação do elemento de `Root` , o código que recebe o elemento de `Child1` de árvore de origem, e o código que transforma os atributos de árvore de origem aos elementos na árvore novo.</span><span class="sxs-lookup"><span data-stu-id="b1d92-125">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>

<span data-ttu-id="b1d92-126">O exemplo funcional, nesse caso, não é mais curto nem mais simples do que o primeiro exemplo.</span><span class="sxs-lookup"><span data-stu-id="b1d92-126">The functional example in this case is neither shorter nor simpler than the first example.</span></span> <span data-ttu-id="b1d92-127">No entanto, se você tiver muitas alterações a serem feitas em uma árvore XML, a abordagem do procedimento se tornará bastante complexa e, de certa forma, obtuso.</span><span class="sxs-lookup"><span data-stu-id="b1d92-127">However, if you have many changes to make to an XML tree, the procedural approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="b1d92-128">Por outro lado, ao usar a abordagem funcional, você ainda forma apenas XML desejado, inserindo consultas e expressões apropriadas, para receber dentro do conteúdo desejado.</span><span class="sxs-lookup"><span data-stu-id="b1d92-128">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="b1d92-129">Os passa funcionais de abordagem código que é mais fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="b1d92-129">The functional approach yields code that is easier to maintain.</span></span>

<span data-ttu-id="b1d92-130">Observe que neste caso a abordagem funcional provavelmente não deseja executar muito bem como a abordagem de manipulação de árvore.</span><span class="sxs-lookup"><span data-stu-id="b1d92-130">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="b1d92-131">O principal problema é que a abordagem funcional cria mais objetos de curta duração.</span><span class="sxs-lookup"><span data-stu-id="b1d92-131">The main issue is that the functional approach creates more short-lived objects.</span></span> <span data-ttu-id="b1d92-132">No entanto, as troca são eficiente usar a abordagem funcional permite maior produtividade do programador.</span><span class="sxs-lookup"><span data-stu-id="b1d92-132">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>

<span data-ttu-id="b1d92-133">Este é um exemplo muito simples, mas serve para mostrar a diferença na filosofia entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="b1d92-133">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="b1d92-134">A abordagem mais funcional fornece ganhos de produtividade para transformar documentos XML maiores.</span><span class="sxs-lookup"><span data-stu-id="b1d92-134">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>
