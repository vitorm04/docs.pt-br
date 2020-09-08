---
title: Como transmitir fragmentos XML de um XmlReader-LINQ to XML
description: Você pode transmitir fragmentos XML de um XmlReader usando um método de eixo personalizado em C# e Visual Basic. Essa é uma abordagem que pode funcionar quando o carregamento da árvore XML inteira na memória é inviável.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e3a7a6260c66f0295216552c6aa56f71a8536bdf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551894"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-linq-to-xml"></a><span data-ttu-id="6af34-104">Como transmitir fragmentos XML de um XmlReader (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6af34-104">How to stream XML fragments from an XmlReader (LINQ to XML)</span></span>

<span data-ttu-id="6af34-105">Quando você tem que processa grandes arquivos XML, talvez não seja possível carregar a árvore inteira XML na memória.</span><span class="sxs-lookup"><span data-stu-id="6af34-105">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="6af34-106">Este artigo mostra como transmitir fragmentos usando um <xref:System.Xml.XmlReader> em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6af34-106">This article shows how to stream fragments using an <xref:System.Xml.XmlReader> in C# and Visual Basic.</span></span>

<span data-ttu-id="6af34-107">Um dos modos de efetivas usar <xref:System.Xml.XmlReader> para ler objetos de <xref:System.Xml.Linq.XElement> é escrever seu próprio método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="6af34-107">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="6af34-108">Um método de eixo normalmente retorna uma coleção, como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> , conforme mostrado no exemplo neste artigo.</span><span class="sxs-lookup"><span data-stu-id="6af34-108">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this article.</span></span> <span data-ttu-id="6af34-109">No método personalizado do eixo, depois de criar o fragmento XML chamando o método <xref:System.Xml.Linq.XNode.ReadFrom%2A> , retornar a coleção usando `yield return`.</span><span class="sxs-lookup"><span data-stu-id="6af34-109">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="6af34-110">Isso fornece a semântica de execução adiada ao método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="6af34-110">This provides deferred execution semantics to your custom axis method.</span></span>

<span data-ttu-id="6af34-111">Quando você cria uma árvore XML de um objeto de <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlReader> deve ser posicionado em um elemento.</span><span class="sxs-lookup"><span data-stu-id="6af34-111">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="6af34-112">O <xref:System.Xml.Linq.XNode.ReadFrom%2A> método não retorna até que ele leia a marca de fechamento do elemento.</span><span class="sxs-lookup"><span data-stu-id="6af34-112">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method doesn't return until it has read the close tag of the element.</span></span>

<span data-ttu-id="6af34-113">Se você desejar criar uma árvore parcial, você pode criar uma instância <xref:System.Xml.XmlReader>, posiciona o leitor no nó que você deseja converter a <xref:System.Xml.Linq.XElement> uma árvore e em seguida, cria o objeto de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="6af34-113">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>

<span data-ttu-id="6af34-114">O artigo [como transmitir fragmentos XML com acesso a informações de cabeçalho](stream-xml-fragments-access-header-information.md) contém informações sobre como transmitir um documento mais complexo.</span><span class="sxs-lookup"><span data-stu-id="6af34-114">The article [How to stream XML fragments with access to header information](stream-xml-fragments-access-header-information.md) contains information on streaming a more complex document.</span></span>

<span data-ttu-id="6af34-115">O artigo [como executar a transformação de streaming de documentos XML grandes](perform-streaming-transform-large-xml-documents.md) contém um exemplo de como usar LINQ to XML para transformar documentos XML extremamente grandes enquanto mantém uma pequena superfície de memória.</span><span class="sxs-lookup"><span data-stu-id="6af34-115">The article [How to perform streaming transform of large XML documents](perform-streaming-transform-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>

## <a name="example-create-a-custom-axis-method"></a><span data-ttu-id="6af34-116">Exemplo: criar um método de eixo personalizado</span><span class="sxs-lookup"><span data-stu-id="6af34-116">Example: Create a custom axis method</span></span>

<span data-ttu-id="6af34-117">Este exemplo cria um método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="6af34-117">This example creates a custom axis method.</span></span> <span data-ttu-id="6af34-118">Você pode consultá-lo usando uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="6af34-118">You can query it by using a LINQ query.</span></span> <span data-ttu-id="6af34-119">O método Axis personalizado `StreamRootChildDoc` pode ler um documento que tem um elemento repetitivo `Child` .</span><span class="sxs-lookup"><span data-stu-id="6af34-119">The custom axis method `StreamRootChildDoc` can read a document that has a repeating `Child` element.</span></span>

```csharp
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)
{
    using (XmlReader reader = XmlReader.Create(stringReader))
    {
        reader.MoveToContent();
        // Parse the file and display each of the nodes.
        while (reader.Read())
        {
            switch (reader.NodeType)
            {
                case XmlNodeType.Element:
                    if (reader.Name == "Child") {
                        XElement el = XElement.ReadFrom(reader) as XElement;
                        if (el != null)
                            yield return el;
                    }
                    break;
            }
        }
    }
}

static void Main(string[] args)
{
    string markup = @"<Root>
      <Child Key=""01"">
        <GrandChild>aaa</GrandChild>
      </Child>
      <Child Key=""02"">
        <GrandChild>bbb</GrandChild>
      </Child>
      <Child Key=""03"">
        <GrandChild>ccc</GrandChild>
      </Child>
    </Root>";

    IEnumerable<string> grandChildData =
        from el in StreamRootChildDoc(new StringReader(markup))
        where (int)el.Attribute("Key") > 1
        select (string)el.Element("GrandChild");

    foreach (string str in grandChildData) {
        Console.WriteLine(str);
    }
}
```

```vb
Module Module1
    Sub Main()
        Dim markup = "<Root>" &
                     "  <Child Key=""01"">" &
                     "    <GrandChild>aaa</GrandChild>" &
                     "  </Child>" &
                     "  <Child Key=""02"">" &
                     "    <GrandChild>bbb</GrandChild>" &
                     "  </Child>" &
                     "  <Child Key=""03"">" &
                     "    <GrandChild>ccc</GrandChild>" &
                     "  </Child>" &
                     "</Root>"

        Dim grandChildData =
             From el In New StreamRootChildDoc(New IO.StringReader(markup))
             Where CInt(el.@Key) > 1
             Select el.<GrandChild>.Value

        For Each s In grandChildData
            Console.WriteLine(s)
        Next
    End Sub
End Module

Public Class StreamRootChildDoc
    Implements IEnumerable(Of XElement)

    Private _stringReader As IO.StringReader

    Public Sub New(ByVal stringReader As IO.StringReader)
        _stringReader = stringReader
    End Sub

    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator
        Return New StreamChildEnumerator(_stringReader)
    End Function

    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator
        Return Me.GetEnumerator()
    End Function
End Class

Public Class StreamChildEnumerator
    Implements IEnumerator(Of XElement)

    Private _current As XElement
    Private _reader As Xml.XmlReader
    Private _stringReader As IO.StringReader

    Public Sub New(ByVal stringReader As IO.StringReader)
        _stringReader = stringReader
        _reader = Xml.XmlReader.Create(_stringReader)
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
        While _reader.Read()
            Select Case _reader.NodeType
                Case Xml.XmlNodeType.Element
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)
                    If el IsNot Nothing Then
                        _current = el
                        Return True
                    End If
            End Select
        End While

        Return False
    End Function

    Public Sub Reset() Implements IEnumerator.Reset
        _reader = Xml.XmlReader.Create(_stringReader)
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

<span data-ttu-id="6af34-120">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="6af34-120">This example produces the following output:</span></span>

```output
bbb
ccc
```

<span data-ttu-id="6af34-121">A técnica usada neste exemplo mantém um pequeno volume de memória até mesmo para milhões de `Child` elementos.</span><span class="sxs-lookup"><span data-stu-id="6af34-121">The technique used in this example maintains a small memory footprint even for millions of `Child` elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="6af34-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="6af34-122">See also</span></span>

- [<span data-ttu-id="6af34-123">Análise XML</span><span class="sxs-lookup"><span data-stu-id="6af34-123">Parse XML</span></span>](parse-string.md)
