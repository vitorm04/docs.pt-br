---
title: Como trabalhar com dicionários usando LINQ to XML-LINQ to XML
description: Você pode converter muitos tipos de estruturas de dados em XML e pode converter XML em estruturas. Aqui está um exemplo que converte um. Dictionary genérico em XML e vice-versa.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: ea61a79549488765526f45852dae7a4df7cacb64
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551948"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml"></a><span data-ttu-id="223e0-104">Como trabalhar com dicionários usando LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="223e0-104">How to work with dictionaries using LINQ to XML</span></span>

<span data-ttu-id="223e0-105">Geralmente, é conveniente converter as estruturas de dados de vários tipos em XML e, em seguida, de XML para outras estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="223e0-105">It's often convenient to convert data structures of various kinds to XML, and then from XML to other data structures.</span></span> <span data-ttu-id="223e0-106">Este artigo mostra uma conversão de um <xref:System.Collections.Generic.Dictionary%602> para XML e de volta.</span><span class="sxs-lookup"><span data-stu-id="223e0-106">This article shows a conversion of a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>

## <a name="example-create-a-dictionary-and-convert-its-contents-to-xml"></a><span data-ttu-id="223e0-107">Exemplo: criar um dicionário e converter seu conteúdo em XML</span><span class="sxs-lookup"><span data-stu-id="223e0-107">Example: Create a Dictionary and convert its contents to XML</span></span>

<span data-ttu-id="223e0-108">Este primeiro exemplo cria um <xref:System.Collections.Generic.Dictionary%602> e, em seguida, converte-o em XML.</span><span class="sxs-lookup"><span data-stu-id="223e0-108">This first example creates a <xref:System.Collections.Generic.Dictionary%602>, and then converts it to XML.</span></span>

<span data-ttu-id="223e0-109">Esta versão C# do exemplo usa uma forma de construção funcional em que uma consulta projeta novos <xref:System.Xml.Linq.XElement> objetos e a coleção resultante é passada como um argumento para o construtor do <xref:System.Xml.Linq.XElement> objeto raiz.</span><span class="sxs-lookup"><span data-stu-id="223e0-109">This C# version of the example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>

<span data-ttu-id="223e0-110">A versão Visual Basic usa literais XML e uma consulta em uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="223e0-110">The Visual Basic version uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="223e0-111">A consulta projeta novos <xref:System.Xml.Linq.XElement> objetos que se tornam o novo conteúdo do `Root` <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="223e0-111">The query projects new <xref:System.Xml.Linq.XElement> objects which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>

```csharp
Dictionary<string, string> dict = new Dictionary<string, string>();
dict.Add("Child1", "Value1");
dict.Add("Child2", "Value2");
dict.Add("Child3", "Value3");
dict.Add("Child4", "Value4");
XElement root = new XElement("Root",
    from keyValue in dict
    select new XElement(keyValue.Key, keyValue.Value)
);
Console.WriteLine(root);
```

```vb
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()
dict.Add("Child1", "Value1")
dict.Add("Child2", "Value2")
dict.Add("Child3", "Value3")
dict.Add("Child4", "Value4")
Dim root As XElement = _
    <Root>
        <%= From keyValue In dict _
            Select New XElement(keyValue.Key, keyValue.Value) %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="223e0-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="223e0-112">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Value1</Child1>
  <Child2>Value2</Child2>
  <Child3>Value3</Child3>
  <Child4>Value4</Child4>
</Root>
```

## <a name="example-create-a-dictionary-and-load-it-from-xml-data"></a><span data-ttu-id="223e0-113">Exemplo: criar um dicionário e carregá-lo a partir de dados XML</span><span class="sxs-lookup"><span data-stu-id="223e0-113">Example: Create a dictionary and load it from XML data</span></span>

<span data-ttu-id="223e0-114">O exemplo a seguir cria uma carga de dicionário carregada a partir de dados XML.</span><span class="sxs-lookup"><span data-stu-id="223e0-114">The next example creates a dictionary loads loads it from XML data.</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", "Value1"),
    new XElement("Child2", "Value2"),
    new XElement("Child3", "Value3"),
    new XElement("Child4", "Value4")
);

Dictionary<string, string> dict = new Dictionary<string, string>();
foreach (XElement el in root.Elements())
    dict.Add(el.Name.LocalName, el.Value);
foreach (string str in dict.Keys)
    Console.WriteLine("{0}:{1}", str, dict[str]);
```

```vb
Dim root As XElement = _
        <Root>
            <Child1>Value1</Child1>
            <Child2>Value2</Child2>
            <Child3>Value3</Child3>
            <Child4>Value4</Child4>
        </Root>

Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)
For Each el As XElement In root.Elements
    dict.Add(el.Name.LocalName, el.Value)
Next
For Each str As String In dict.Keys
    Console.WriteLine("{0}:{1}", str, dict(str))
Next
```

<span data-ttu-id="223e0-115">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="223e0-115">This example produces the following output:</span></span>

```output
Child1:Value1
Child2:Value2
Child3:Value3
Child4:Value4
```

## <a name="see-also"></a><span data-ttu-id="223e0-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="223e0-116">See also</span></span>

- [<span data-ttu-id="223e0-117">Projeções e transformações (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="223e0-117">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
