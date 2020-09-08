---
title: Pré-atomização de objetos XName-LINQ to XML
description: Saiba como pré-testar o Atom para melhorar o desempenho ao criar um grande número de elementos com o mesmo nome.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 97da1e09e246491d8427c7a69953e006c80475a4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551907"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml"></a><span data-ttu-id="6380e-103">Pré-atomização de objetos XName (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6380e-103">Pre-Atomization of XName objects (LINQ to XML)</span></span>

<span data-ttu-id="6380e-104">Uma maneira para melhorar o desempenho em LINQ to XML é pré-compilação atomizar objetos de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="6380e-104">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="6380e-105">a pré-compilação atomização significa que você atribuir uma cadeia de caracteres a um objeto de <xref:System.Xml.Linq.XName> antes de criar a árvore XML usando os construtores de classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="6380e-105">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="6380e-106">Em seguida, em vez de passar uma cadeia de caracteres para o construtor, que usaria a conversão implícita de cadeia de caracteres a <xref:System.Xml.Linq.XName>, você passa o objeto inicializado de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="6380e-106">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>

<span data-ttu-id="6380e-107">Isso melhora o desempenho quando você cria uma árvore XML grande na qual os nomes são repetidos.</span><span class="sxs-lookup"><span data-stu-id="6380e-107">This improves performance when you create a large XML tree in which names are repeated.</span></span> <span data-ttu-id="6380e-108">Para fazer isso, você declarar e inicializar objetos de <xref:System.Xml.Linq.XName> antes que você construa a árvore XML e em seguida, usar objetos de <xref:System.Xml.Linq.XName> em vez de especificar cadeias de caracteres para nomes de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="6380e-108">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="6380e-109">Essa técnica pode gerar ganhos de desempenho significativos se você estiver criando um grande número de elementos ou atributos com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="6380e-109">This technique can yield significant performance gains if you're creating a large number of elements or attributes with the same name.</span></span>

<span data-ttu-id="6380e-110">Você deve testar a pré-compilação atomização com seu cenário para decidir se você usar o.</span><span class="sxs-lookup"><span data-stu-id="6380e-110">You should test pre-atomization with your scenario to decide if you should use it.</span></span>

## <a name="example-create-elements-in-various-ways-with-and-without-pre-atomization"></a><span data-ttu-id="6380e-111">Exemplo: criar elementos de várias maneiras, com e sem a pré-atomização</span><span class="sxs-lookup"><span data-stu-id="6380e-111">Example: Create elements in various ways, with and without pre-atomization</span></span>

<span data-ttu-id="6380e-112">O exemplo a seguir demonstra a pré-atomização.</span><span class="sxs-lookup"><span data-stu-id="6380e-112">The following example demonstrates pre-atomization.</span></span>

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

<span data-ttu-id="6380e-113">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="6380e-113">This example produces the following output:</span></span>

```xml
<Root>
  <Data ID="1">4,100,000</Data>
  <Data ID="2">3,700,000</Data>
  <Data ID="3">1,150,000</Data>
</Root>
```

<span data-ttu-id="6380e-114">O exemplo a seguir mostra a mesma técnica para um documento XML em um namespace:</span><span class="sxs-lookup"><span data-stu-id="6380e-114">The following example shows the same technique for an XML document in a namespace:</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XName Root = aw + "Root";
XName Data = aw + "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XAttribute(XNamespace.Xmlns + "aw", aw),
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

```vb
Dim aw As XNamespace = "http://www.adventure-works.com"
Dim root1 As XName = aw + "Root"
Dim data As XName = aw + "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XAttribute(XNamespace.Xmlns + "aw", aw),
                          New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

<span data-ttu-id="6380e-115">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="6380e-115">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Data ID="1">4,100,000</aw:Data>
  <aw:Data ID="2">3,700,000</aw:Data>
  <aw:Data ID="3">1,150,000</aw:Data>
</aw:Root>
```

<span data-ttu-id="6380e-116">O exemplo a seguir é mais semelhante ao que você provavelmente encontrará no mundo real.</span><span class="sxs-lookup"><span data-stu-id="6380e-116">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="6380e-117">Nesse exemplo, o conteúdo do elemento é fornecido por uma consulta:</span><span class="sxs-lookup"><span data-stu-id="6380e-117">In this example, the content of the element is supplied by a query:</span></span>

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

DateTime t1 = DateTime.Now;
XElement root = new XElement(Root,
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement(Data,
        new XAttribute(ID, i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root2 As New XElement(root1, From i In Enumerable.Range(1, 100000)
                                 Select New XElement(data, New XAttribute(ID, i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

<span data-ttu-id="6380e-118">O exemplo anterior tem um desempenho melhor do que o exemplo a seguir, em que os nomes não são previamente atomos:</span><span class="sxs-lookup"><span data-stu-id="6380e-118">The previous example performs better than the following example, in which names aren't pre-atomized:</span></span>

```csharp
DateTime t1 = DateTime.Now;
XElement root = new XElement("Root",
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement("Data",
        new XAttribute("ID", i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a><span data-ttu-id="6380e-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="6380e-119">See also</span></span>

- [<span data-ttu-id="6380e-120">Objetos XName e XNamespace atomos</span><span class="sxs-lookup"><span data-stu-id="6380e-120">Atomized XName and XNamespace objects</span></span>](atomized-xname-xnamespace-objects.md)
