---
title: Modificação da árvore XML na memória versus construção funcional (LINQ to XML) (C#)
description: Esses exemplos alteram a forma de um documento XML modificando-o no local e usando LINQ to XML construção funcional em C#.
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 7a2e3d2ddcd452cf6a58e9d5cc886f3e8b8dd325
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165786"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="39a4a-103">Modificação da árvore XML na memória versus construção funcional (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="39a4a-103">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="39a4a-104">Modificar uma árvore XML no local é uma abordagem tradicional para alterar a forma de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="39a4a-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="39a4a-105">Um aplicativo típico carregar um documento em um armazenamento de dados como os DOM ou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; usa uma interface de programação para inserir nós, nós, excluir ou modificar o conteúdo dos nós; e então salva XML para um arquivo ou fluxo em uma rede.</span><span class="sxs-lookup"><span data-stu-id="39a4a-105">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 <span data-ttu-id="39a4a-106">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permite outra abordagem que é útil em muitos cenários: *construção funcional*.</span><span class="sxs-lookup"><span data-stu-id="39a4a-106">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="39a4a-107">Deleites funcionais de compilação que modificam dados como um problema de transformação, em vez de como tratamento detalhada de um armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="39a4a-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="39a4a-108">Se você pode ter uma representação dos dados e a transformação com eficiência de um formulário para outro, o resultado é o mesmo como se você recebe um armazenamento de dados e o manipulou de alguma maneira para executar outra forma.</span><span class="sxs-lookup"><span data-stu-id="39a4a-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="39a4a-109">Uma chave para a abordagem de construção funcional é passar os resultados de consultas para os construtores <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="39a4a-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="39a4a-110">Em muitos casos você pode escrever código transformacional em uma fração de tempo que iria para manipular o armazenamento de dados, e que o código é mais fácil e mais robusto manter.</span><span class="sxs-lookup"><span data-stu-id="39a4a-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="39a4a-111">Nesses casos, mesmo que a abordagem transformacional pode levar mais avançados de processamento, é mais eficiente para modificar dados.</span><span class="sxs-lookup"><span data-stu-id="39a4a-111">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="39a4a-112">Se um desenvolvedor estiver familiarizado com a abordagem funcional, o código resultante é em muitos casos mais fácil de entender.</span><span class="sxs-lookup"><span data-stu-id="39a4a-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="39a4a-113">É mais fácil de localizar o código que altera cada parte da árvore.</span><span class="sxs-lookup"><span data-stu-id="39a4a-113">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="39a4a-114">A abordagem onde você altera uma árvore XML no local é mais familiar para muitos desenvolvedores DOM, enquanto o código escrito usando a abordagem funcional pode parecer estranha a um desenvolvedor que não entende ainda essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="39a4a-114">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="39a4a-115">Se você precisa apenas fazer uma alteração pequena a uma grande árvore XML, a abordagem onde você altera uma árvore no lugar em muitos casos terá menos processador central - tempo.</span><span class="sxs-lookup"><span data-stu-id="39a4a-115">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="39a4a-116">Este tópico fornece um exemplo que é implementado com as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="39a4a-116">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="39a4a-117">Transformando atributos em elementos</span><span class="sxs-lookup"><span data-stu-id="39a4a-117">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="39a4a-118">Para esse exemplo, suponha que você deseja modificar o seguinte documento XML simples de modo que os atributos se transformem elementos.</span><span class="sxs-lookup"><span data-stu-id="39a4a-118">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="39a4a-119">Este tópico apresenta primeiro a abordagem no lugar tradicional de alteração.</span><span class="sxs-lookup"><span data-stu-id="39a4a-119">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="39a4a-120">Mostra a abordagem funcional de compilação.</span><span class="sxs-lookup"><span data-stu-id="39a4a-120">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="39a4a-121">Alterando a árvore XML</span><span class="sxs-lookup"><span data-stu-id="39a4a-121">Modifying the XML Tree</span></span>  
 <span data-ttu-id="39a4a-122">Você pode escrever qualquer código procedural para criar elementos de atributos, e exclui os atributos, como segue:</span><span class="sxs-lookup"><span data-stu-id="39a4a-122">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="39a4a-123">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="39a4a-123">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="39a4a-124">Abordagem funcional de compilação</span><span class="sxs-lookup"><span data-stu-id="39a4a-124">Functional Construction Approach</span></span>  
 <span data-ttu-id="39a4a-125">Por outro lado, uma abordagem funcional consiste no código para formar uma nova árvore, a recortagem e escolha elementos e atributos de árvore de origem, e transformar-los tão apropriados como são adicionados à nova árvore.</span><span class="sxs-lookup"><span data-stu-id="39a4a-125">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="39a4a-126">Os aspectos funcionais de abordagem parece com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="39a4a-126">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="39a4a-127">Saída deste exemplo mesmo XML que o primeiro exemplo.</span><span class="sxs-lookup"><span data-stu-id="39a4a-127">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="39a4a-128">No entanto, observe que você pode realmente consulte a estrutura XML resultante de novo na abordagem funcional.</span><span class="sxs-lookup"><span data-stu-id="39a4a-128">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="39a4a-129">Você pode ver a criação do elemento de `Root` , o código que recebe o elemento de `Child1` de árvore de origem, e o código que transforma os atributos de árvore de origem aos elementos na árvore novo.</span><span class="sxs-lookup"><span data-stu-id="39a4a-129">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="39a4a-130">O exemplo funcional não nesse caso é menor que o primeiro exemplo, e não é realmente mais simples.</span><span class="sxs-lookup"><span data-stu-id="39a4a-130">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="39a4a-131">No entanto, se você tiver muitas alterações para fazer a uma árvore XML, a abordagem não funcional será muito complexa e um pouco obtuso.</span><span class="sxs-lookup"><span data-stu-id="39a4a-131">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="39a4a-132">Por outro lado, ao usar a abordagem funcional, você ainda forma apenas XML desejado, inserindo consultas e expressões apropriadas, para receber dentro do conteúdo desejado.</span><span class="sxs-lookup"><span data-stu-id="39a4a-132">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="39a4a-133">Os passa funcionais de abordagem código que é mais fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="39a4a-133">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="39a4a-134">Observe que neste caso a abordagem funcional provavelmente não deseja executar muito bem como a abordagem de manipulação de árvore.</span><span class="sxs-lookup"><span data-stu-id="39a4a-134">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="39a4a-135">A principal problema é que a abordagem funcional cria um objetos mais breves.</span><span class="sxs-lookup"><span data-stu-id="39a4a-135">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="39a4a-136">No entanto, as troca são eficiente usar a abordagem funcional permite maior produtividade do programador.</span><span class="sxs-lookup"><span data-stu-id="39a4a-136">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="39a4a-137">Este é um exemplo muito simples, mas serve para mostrar a diferença na filosofia entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="39a4a-137">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="39a4a-138">A abordagem mais funcional fornece ganhos de produtividade para transformar documentos XML maiores.</span><span class="sxs-lookup"><span data-stu-id="39a4a-138">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  