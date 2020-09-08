---
title: Como executar a transformação de streaming de documentos XML grandes-LINQ to XML
description: Saiba como executar a transformação de streaming de documentos XML grandes para atingir um pequeno volume de memória.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: f4dc6613d53580050450d11e51fcbf82ddc7517a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552290"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-linq-to-xml"></a><span data-ttu-id="b46e0-103">Como executar a transformação de streaming de documentos XML grandes (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b46e0-103">How to perform streaming transform of large XML documents (LINQ to XML)</span></span>

<span data-ttu-id="b46e0-104">Às vezes você precisa transformar grandes arquivos XML e escrever seu aplicativo de modo que os requisitos de memória do aplicativo sejam previsíveis.</span><span class="sxs-lookup"><span data-stu-id="b46e0-104">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="b46e0-105">Se você tentar preencher uma árvore XML com um arquivo XML muito grande, seu uso de memória será proporcional ao tamanho do arquivo (isto é, excessivo).</span><span class="sxs-lookup"><span data-stu-id="b46e0-105">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="b46e0-106">Portanto, você deve usar uma técnica de streaming em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b46e0-106">Therefore, you should use a streaming technique instead.</span></span>

<span data-ttu-id="b46e0-107">As técnicas de streaming são melhor aplicadas em situações onde você precisa processar o documento de origem apenas uma vez e você pode processar os elementos na ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="b46e0-107">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="b46e0-108">Determinados operadores de consulta padrão, como <xref:System.Linq.Enumerable.OrderBy%2A>, iteram sua origem, coletam todos os dados, classificam e, em seguida, geram finalmente o primeiro item na sequência.</span><span class="sxs-lookup"><span data-stu-id="b46e0-108">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="b46e0-109">Observe que, se você usar um operador de consulta que materializa sua fonte antes de produzir o primeiro item, você não manterá uma pequena superfície de memória para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b46e0-109">Note that if you use a query operator that materializes its source before yielding the first item, you won't retain a small memory footprint for your application.</span></span>

<span data-ttu-id="b46e0-110">Mesmo que você use a técnica descrita em [como transmitir fragmentos XML com acesso a informações de cabeçalho](stream-xml-fragments-access-header-information.md), se tentar montar uma árvore XML que contém o documento transformado, o uso de memória será muito grande.</span><span class="sxs-lookup"><span data-stu-id="b46e0-110">Even if you use the technique described in [How to stream XML fragments with access to header information](stream-xml-fragments-access-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>

<span data-ttu-id="b46e0-111">Há duas principais abordagens.</span><span class="sxs-lookup"><span data-stu-id="b46e0-111">There are two main approaches.</span></span> <span data-ttu-id="b46e0-112">Uma abordagem é usar as características de processamento adiado de <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="b46e0-112">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="b46e0-113">Outra abordagem é criar um <xref:System.Xml.XmlWriter> e usar os recursos de LINQ to XML para gravar elementos em um <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="b46e0-113">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of LINQ to XML to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="b46e0-114">Este artigo demonstra as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="b46e0-114">This article demonstrates both approaches.</span></span>

## <a name="example-use-the-deferred-execution-capabilities-of-xstreamingelement-to-stream-the-output"></a><span data-ttu-id="b46e0-115">Exemplo: usar os recursos de execução adiada do `XStreamingElement` para transmitir a saída</span><span class="sxs-lookup"><span data-stu-id="b46e0-115">Example: Use the deferred execution capabilities of `XStreamingElement` to stream the output</span></span>

<span data-ttu-id="b46e0-116">O exemplo a seguir baseia-se no exemplo em [como transmitir fragmentos XML com acesso a informações de cabeçalho](stream-xml-fragments-access-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="b46e0-116">The following example builds on the example in [How to stream XML fragments with access to header information](stream-xml-fragments-access-header-information.md).</span></span>

<span data-ttu-id="b46e0-117">Este exemplo usa os recursos de execução adiada de <xref:System.Xml.Linq.XStreamingElement> para transmitir a saída.</span><span class="sxs-lookup"><span data-stu-id="b46e0-117">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="b46e0-118">Este exemplo pode transformar um documento muito grande mantendo um requisito pequeno de memória.</span><span class="sxs-lookup"><span data-stu-id="b46e0-118">This example can transform a very large document while maintaining a small memory footprint.</span></span>

<span data-ttu-id="b46e0-119">Observe que o eixo personalizado (`StreamCustomerItem`) é escrito especificamente para esperar um documento que tem os elementos `Customer`, `Name` e `Item`, e que esses elementos serão organizados como no documento Source.xml a seguir.</span><span class="sxs-lookup"><span data-stu-id="b46e0-119">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="b46e0-120">Uma implementação mais robusta, no entanto, seria preparada para analisar um documento inválido.</span><span class="sxs-lookup"><span data-stu-id="b46e0-120">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>

<span data-ttu-id="b46e0-121">Veja a seguir o documento de origem, Source.xml:</span><span class="sxs-lookup"><span data-stu-id="b46e0-121">The following is the source document, Source.xml:</span></span>

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
        // Loop through Customer elements.
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

                // loop through Item elements
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.EndElement)
                        break;
                    if (reader.NodeType == XmlNodeType.Element
                        && reader.Name == "Item")
                    {
                        item = XElement.ReadFrom(reader) as XElement;
                        if (item != null)
                        {
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
    XStreamingElement root = new XStreamingElement("Root",
        from el in StreamCustomerItem("Source.xml")
        select new XElement("Item",
            new XElement("Customer", (string)el.Parent.Element("Name")),
            new XElement(el.Element("Key"))
        )
    );
    root.Save("Test.xml");
    Console.WriteLine(File.ReadAllText("Test.xml"));
}
```

```vb
Module Module1
    Sub Main()
        Dim root = New XStreamingElement("Root",
            From el In New StreamCustomerItem("Source.xml")
            Select <Item>
                       <Customer><%= el.Parent.<Name>.Value %></Customer>
                       <%= el.<Key> %>
                   </Item>
            )
        root.Save("Test.xml")
        Console.WriteLine(My.Computer.FileSystem.ReadAllText("Test.xml"))
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

<span data-ttu-id="b46e0-122">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b46e0-122">This example produces the following output:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Root>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0001</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0002</Key>
  </Item>
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
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0008</Key>
  </Item>
  <Item>
    <Customer>Southridge Video</Customer>
    <Key>0009</Key>
  </Item>
  <Item>
    <Customer>Southridge Video</Customer>
    <Key>0010</Key>
  </Item>
</Root>
```

## <a name="example-use-linq-to-xml-to-write-elements-to-an-xmlwriter"></a><span data-ttu-id="b46e0-123">Exemplo: usar LINQ to XML para gravar elementos em um XmlWriter</span><span class="sxs-lookup"><span data-stu-id="b46e0-123">Example: Use LINQ to XML to write elements to an XmlWriter</span></span>

<span data-ttu-id="b46e0-124">O exemplo a seguir também se baseia no exemplo em [como transmitir fragmentos XML com acesso a informações de cabeçalho](stream-xml-fragments-access-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="b46e0-124">The following example also builds on the example in [How to stream XML fragments with access to header information](stream-xml-fragments-access-header-information.md).</span></span>

<span data-ttu-id="b46e0-125">Este exemplo usa a funcionalidade de LINQ to XML para gravar elementos em um <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="b46e0-125">This example uses the capability of LINQ to XML to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="b46e0-126">Este exemplo pode transformar um documento muito grande mantendo um requisito pequeno de memória.</span><span class="sxs-lookup"><span data-stu-id="b46e0-126">This example can transform a very large document while maintaining a small memory footprint.</span></span>

<span data-ttu-id="b46e0-127">Observe que o eixo personalizado (`StreamCustomerItem`) é escrito especificamente para esperar um documento que tem os elementos `Customer`, `Name` e `Item`, e que esses elementos serão organizados como no documento Source.xml a seguir.</span><span class="sxs-lookup"><span data-stu-id="b46e0-127">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="b46e0-128">Uma implementação mais robusta, no entanto, validaria o documento de origem com um XSD ou seria preparada para analisar um documento inválido.</span><span class="sxs-lookup"><span data-stu-id="b46e0-128">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>

<span data-ttu-id="b46e0-129">Este exemplo usa o mesmo documento de origem, Source.xml, como o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="b46e0-129">This example uses the same source document, Source.xml, as the previous example.</span></span> <span data-ttu-id="b46e0-130">Ele também produz exatamente a mesma saída.</span><span class="sxs-lookup"><span data-stu-id="b46e0-130">It also produces exactly the same output.</span></span>

<span data-ttu-id="b46e0-131">Usando <xref:System.Xml.Linq.XStreamingElement> for streaming, o XML de saída é preferencial para gravar em um <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="b46e0-131">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred to writing to an <xref:System.Xml.XmlWriter>.</span></span>

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
        // Loop through Customer elements.
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
    IEnumerable<XElement> srcTree =
        from el in StreamCustomerItem("Source.xml")
        select new XElement("Item",
            new XElement("Customer", (string)el.Parent.Element("Name")),
            new XElement(el.Element("Key"))
        );
    XmlWriterSettings xws = new XmlWriterSettings();
    xws.OmitXmlDeclaration = true;
    xws.Indent = true;
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {
        xw.WriteStartElement("Root");
        foreach (XElement el in srcTree)
            el.WriteTo(xw);
        xw.WriteEndElement();
    }

    string str = File.ReadAllText("Output.xml");
    Console.WriteLine(str);
}
```

```vb
Module Module1
    Sub Main()
        Dim srcTree =
            From el In New StreamCustomerItem("Source.xml")
            Select <Item>
                       <Customer><%= el.Parent.<Name>.Value %></Customer>
                       <%= el.<Key> %>
                   </Item>

        Dim xws = New Xml.XmlWriterSettings()
        xws.OmitXmlDeclaration = True
        xws.Indent = True
        Using xw = Xml.XmlWriter.Create("Output.xml", xws)
            xw.WriteStartElement("Root")
            For Each el In srcTree
                el.WriteTo(xw)
            Next
            xw.WriteEndElement()
        End Using

        Dim s = My.Computer.FileSystem.ReadAllText("Output.xml")
        Console.WriteLine(s)
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

<span data-ttu-id="b46e0-132">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b46e0-132">This example produces the following output:</span></span>

```xml
<Root>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0001</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0002</Key>
  </Item>
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
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0008</Key>
  </Item>
  <Item>
    <Customer>Southridge Video</Customer>
    <Key>0009</Key>
  </Item>
  <Item>
    <Customer>Southridge Video</Customer>
    <Key>0010</Key>
  </Item>
</Root>
```
