---
title: Como transmitir fragmentos XML com acesso a informações de cabeçalho-LINQ to XML
description: Saiba como implementar e usar um método de eixo personalizado que transmite fragmentos XML do arquivo especificado por um URI.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: d50c29feb305341155257cd215e0292350689e7b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551958"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-linq-to-xml"></a><span data-ttu-id="c7748-103">Como transmitir fragmentos XML com acesso a informações de cabeçalho (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c7748-103">How to stream XML fragments with access to header information (LINQ to XML)</span></span>

<span data-ttu-id="c7748-104">Às vezes você precisará ler arbitrariamente grandes arquivos XML, e escreve seu aplicativo para que os vestígio de memória do aplicativo seja previsível.</span><span class="sxs-lookup"><span data-stu-id="c7748-104">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="c7748-105">Se você tentar preencher uma árvore XML com um grande arquivo XML, seu uso de memória será proporcionalmente o tamanho do arquivo que é, excessivo.</span><span class="sxs-lookup"><span data-stu-id="c7748-105">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="c7748-106">Portanto, você deve usar uma técnica de streaming em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c7748-106">Therefore, you should use a streaming technique instead.</span></span>

<span data-ttu-id="c7748-107">Uma opção é escrever seu aplicativo usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c7748-107">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c7748-108">No entanto, talvez você queira usar o LINQ para consultar a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="c7748-108">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="c7748-109">Nesse caso, você pode escrever seu próprio método de eixo personalizado.</span><span class="sxs-lookup"><span data-stu-id="c7748-109">If so, you can write your own custom axis method.</span></span> <span data-ttu-id="c7748-110">Para obter mais informações, consulte [como escrever um método de eixo de LINQ to XML](write-linq-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="c7748-110">For more information, see [How to write a LINQ to XML axis method](write-linq-xml-axis-method.md).</span></span>

<span data-ttu-id="c7748-111">Para escrever seu próprio método de eixo, você escreve um método pequeno que usa os <xref:System.Xml.XmlReader> nós para ler até atingir um dos nós nos quais você está interessado.</span><span class="sxs-lookup"><span data-stu-id="c7748-111">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you're interested.</span></span> <span data-ttu-id="c7748-112">O método chama em <xref:System.Xml.Linq.XNode.ReadFrom%2A>, que lê de <xref:System.Xml.XmlReader> e cria uma instância de um fragmento XML.</span><span class="sxs-lookup"><span data-stu-id="c7748-112">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="c7748-113">Em seguida, ele gera cada fragmento até `yield return` o método que está enumerando seu método de eixo personalizado.</span><span class="sxs-lookup"><span data-stu-id="c7748-113">It then yields each fragment through `yield return` to the method that's enumerating your custom axis method.</span></span> <span data-ttu-id="c7748-114">Você pode escrever consultas LINQ no método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="c7748-114">You can then write LINQ queries on your custom axis method.</span></span>

<span data-ttu-id="c7748-115">As técnicas de streaming são melhor aplicadas em situações onde você precisa processar o documento de origem apenas uma vez e você pode processar os elementos na ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="c7748-115">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="c7748-116">Determinados operadores de consulta padrão, como <xref:System.Linq.Enumerable.OrderBy%2A>, iteram sua origem, coletam todos os dados, classificam e, em seguida, geram finalmente o primeiro item na sequência.</span><span class="sxs-lookup"><span data-stu-id="c7748-116">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="c7748-117">Se você usar um operador de consulta que materializa sua fonte antes de gerar o primeiro item, você não manterá uma pequena superfície de memória.</span><span class="sxs-lookup"><span data-stu-id="c7748-117">If you use a query operator that materializes its source before yielding the first item, you won't retain a small memory footprint.</span></span>

## <a name="example-implement-and-use-a-custom-axis-method-that-streams-xml-fragments-from-the-file-specified-by-a-uri"></a><span data-ttu-id="c7748-118">Exemplo: implementar e usar um método de eixo personalizado que transmite fragmentos XML do arquivo especificado por um URI</span><span class="sxs-lookup"><span data-stu-id="c7748-118">Example: Implement and use a custom axis method that streams XML fragments from the file specified by a URI</span></span>

<span data-ttu-id="c7748-119">Às vezes o problema é apenas um pouco mais interessante.</span><span class="sxs-lookup"><span data-stu-id="c7748-119">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="c7748-120">No documento XML a seguir, o consumidor do método personalizado do eixo também precisa saber o nome do cliente que cada item pertence.</span><span class="sxs-lookup"><span data-stu-id="c7748-120">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root>
  <Customer>
    <Name>A. Datum Corporation</Name>
    <Item>
      <Key>0001</Key>
    </Item>
    <Item>
      <Key>0002</Key>
    </Item>
    <Item>
      <Key>0003</Key>
    </Item>
    <Item>
      <Key>0004</Key>
    </Item>
  </Customer>
  <Customer>
    <Name>Fabrikam, Inc.</Name>
    <Item>
      <Key>0005</Key>
    </Item>
    <Item>
      <Key>0006</Key>
    </Item>
    <Item>
      <Key>0007</Key>
    </Item>
    <Item>
      <Key>0008</Key>
    </Item>
  </Customer>
  <Customer>
    <Name>Southridge Video</Name>
    <Item>
      <Key>0009</Key>
    </Item>
    <Item>
      <Key>0010</Key>
    </Item>
  </Customer>
</Root>
```

<span data-ttu-id="c7748-121">A abordagem que esse exemplo leva é também observar essas informações de cabeçalho, salvar as informações de cabeçalho e, em seguida, criar uma pequena árvore XML que contenha as informações de cabeçalho e os detalhes que você está enumerando.</span><span class="sxs-lookup"><span data-stu-id="c7748-121">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you're enumerating.</span></span> <span data-ttu-id="c7748-122">O método do eixo resulta nessa nova árvore, pequena XML.</span><span class="sxs-lookup"><span data-stu-id="c7748-122">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="c7748-123">A consulta possui o acesso a informações de cabeçalho bem como para informações detalhadas.</span><span class="sxs-lookup"><span data-stu-id="c7748-123">The query then has access to the header information as well as the detail information.</span></span>

<span data-ttu-id="c7748-124">Essa abordagem tem uma pegada pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="c7748-124">This approach has a small memory footprint.</span></span> <span data-ttu-id="c7748-125">Como cada fragmento XML de detalhes é produzido, nenhuma referência é mantida no fragmento anterior e está disponível para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7748-125">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it's available for garbage collection.</span></span> <span data-ttu-id="c7748-126">Essa técnica cria muitos objetos de vida curta no heap.</span><span class="sxs-lookup"><span data-stu-id="c7748-126">This technique creates many short lived objects on the heap.</span></span>

<span data-ttu-id="c7748-127">O exemplo a seguir mostra como implementar e usar um método personalizado do eixo que passa fragmentos XML do arquivo especificado por um URI.</span><span class="sxs-lookup"><span data-stu-id="c7748-127">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="c7748-128">Esse eixo personalizado é escrito de modo que ele espera um documento que `Customer` tem `Name` elementos, e `Item` , e que esses elementos serão organizados como no `Source.xml` documento acima.</span><span class="sxs-lookup"><span data-stu-id="c7748-128">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="c7748-129">É uma implementação simplista.</span><span class="sxs-lookup"><span data-stu-id="c7748-129">It's a simplistic implementation.</span></span> <span data-ttu-id="c7748-130">Uma implementação mais robusta seria preparada para analisar um documento válido.</span><span class="sxs-lookup"><span data-stu-id="c7748-130">A more robust implementation would be prepared to parse an invalid document.</span></span>

```csharp
static IEnumerable<XElement> StreamCustomerItem(string uri)
{
    using (XmlReader reader = XmlReader.Create(uri))
    {
        XElement name = null;
        XElement item = null;

        reader.MoveToContent();

        // Parse the file, save header information when encountered, and yield the
        // Item XElement objects as they're created.

        // loop through Customer elements
        while (reader.Read())
        {
            if (reader.NodeType == XmlNodeType.Element
                && reader.Name == "Customer")
            {
                // move to Name element
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.Element &&
                        reader.Name == "Name")
                    {
                        name = XElement.ReadFrom(reader) as XElement;
                        break;
                    }
                }

                // Loop through Item elements
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.EndElement)
                        break;
                    if (reader.NodeType == XmlNodeType.Element
                        && reader.Name == "Item")
                    {
                        item = XElement.ReadFrom(reader) as XElement;
                        if (item != null) {
                            XElement tempRoot = new XElement("Root",
                                new XElement(name)
                            );
                            tempRoot.Add(item);
                            yield return item;
                        }
                    }
                }
            }
        }
    }
}

static void Main(string[] args)
{
    XElement xmlTree = new XElement("Root",
        from el in StreamCustomerItem("Source.xml")
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7
        select new XElement("Item",
            new XElement("Customer", (string)el.Parent.Element("Name")),
            new XElement(el.Element("Key"))
        )
    );
    Console.WriteLine(xmlTree);
}
```

```vb
Module Module1

    Sub Main()
        Dim xmlTree = <Root>
                          <%=
                              From el In New StreamCustomerItem("Source.xml")
                              Let itemKey = CInt(el.<Key>.Value)
                              Where itemKey >= 3 AndAlso itemKey <= 7
                              Select <Item>
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>
                                         <%= el.<Key> %>
                                     </Item>
                          %>
                      </Root>

        Console.WriteLine(xmlTree)
    End Sub

End Module

Public Class StreamCustomerItem
    Implements IEnumerable(Of XElement)

    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
    End Sub

    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator
        Return New StreamCustomerItemEnumerator(_uri)
    End Function

    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator
        Return Me.GetEnumerator()
    End Function
End Class

Public Class StreamCustomerItemEnumerator
    Implements IEnumerator(Of XElement)

    Private _current As XElement
    Private _customerName As String
    Private _reader As Xml.XmlReader
    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
        _reader = Xml.XmlReader.Create(_uri)
        _reader.MoveToContent()
    End Sub

    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current
        Get
            Return _current
        End Get
    End Property

    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current
        Get
            Return Me.Current
        End Get
    End Property

    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext
        Dim item As XElement
        Dim name As XElement

        ' Parse the file, save header information when encountered, and return the
        ' current Item XElement.

        ' loop through Customer elements
        While _reader.Read()
            If _reader.NodeType = Xml.XmlNodeType.Element Then
                Select Case _reader.Name
                    Case "Customer"
                        ' move to Name element
                        While _reader.Read()

                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso
                                _reader.Name = "Name" Then

                                name = TryCast(XElement.ReadFrom(_reader), XElement)
                                _customerName = If(name IsNot Nothing, name.Value, "")
                                Exit While
                            End If

                        End While
                    Case "Item"
                        item = TryCast(XElement.ReadFrom(_reader), XElement)
                        Dim tempRoot = <Root>
                                           <Name><%= _customerName %></Name>
                                           <%= item %>
                                       </Root>
                        _current = item
                        Return True
                End Select
            End If
        End While

        Return False
    End Function

    Public Sub Reset() Implements IEnumerator.Reset
        _reader = Xml.XmlReader.Create(_uri)
        _reader.MoveToContent()
    End Sub

#Region "IDisposable Support"
    Private disposedValue As Boolean ' To detect redundant calls

    ' IDisposable
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)
        If Not Me.disposedValue Then
            If disposing Then
                _reader.Close()
            End If
        End If
        Me.disposedValue = True
    End Sub

    Public Sub Dispose() Implements IDisposable.Dispose
        Dispose(True)
        GC.SuppressFinalize(Me)
    End Sub
#End Region

End Class
```

 <span data-ttu-id="c7748-131">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="c7748-131">This code produces the following output:</span></span>

```xml
<Root>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0003</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0004</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0005</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0006</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0007</Key>
  </Item>
</Root>
```
