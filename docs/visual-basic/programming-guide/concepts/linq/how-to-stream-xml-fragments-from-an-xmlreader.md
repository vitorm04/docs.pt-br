---
title: 'Como: Stream fragmentos XML de um XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: dfc5dfd6d861992861cd9a5b4bd7266d7d24af75
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564630"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="e332c-102">Como: Stream fragmentos XML de um XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e332c-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="e332c-103">Quando você tem que processa grandes arquivos XML, talvez não seja possível carregar a árvore inteira XML na memória.</span><span class="sxs-lookup"><span data-stu-id="e332c-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="e332c-104">Este tópico mostra como passar informações usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="e332c-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="e332c-105">Um dos modos de efetivas usar <xref:System.Xml.XmlReader> para ler objetos de <xref:System.Xml.Linq.XElement> é escrever seu próprio método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="e332c-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="e332c-106">Um método do eixo normalmente retorna uma coleção como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, conforme mostrado no exemplo neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e332c-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="e332c-107">No método personalizado do eixo, depois de criar o fragmento XML chamando o método <xref:System.Xml.Linq.XNode.ReadFrom%2A> , retornar a coleção usando `yield return`.</span><span class="sxs-lookup"><span data-stu-id="e332c-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="e332c-108">Isso fornece a semântica de execução adiada ao método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="e332c-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="e332c-109">Quando você cria uma árvore XML de um objeto de <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlReader> deve ser posicionado em um elemento.</span><span class="sxs-lookup"><span data-stu-id="e332c-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="e332c-110">O método de <xref:System.Xml.Linq.XNode.ReadFrom%2A> não retorna até que lê a marca do elemento.</span><span class="sxs-lookup"><span data-stu-id="e332c-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="e332c-111">Se você desejar criar uma árvore parcial, você pode criar uma instância <xref:System.Xml.XmlReader>, posiciona o leitor no nó que você deseja converter a <xref:System.Xml.Linq.XElement> uma árvore e em seguida, cria o objeto de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="e332c-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="e332c-112">O tópico [como: Stream fragmentos XML com acesso a informações de cabeçalho (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contém informações e um exemplo de como transmitir um documento mais complexo.</span><span class="sxs-lookup"><span data-stu-id="e332c-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="e332c-113">O tópico [como: Executar o fluxo de transformação de grandes documentos XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contém um exemplo de como usar o LINQ to XML para transformar documentos XML muito grandes, mantendo uma pegada pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="e332c-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e332c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e332c-114">Example</span></span>  
 <span data-ttu-id="e332c-115">Este exemplo cria um método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="e332c-115">This example creates a custom axis method.</span></span> <span data-ttu-id="e332c-116">Você pode consultá-lo usando uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e332c-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="e332c-117">O método de eixo personalizado `StreamRootChildDoc` é um método que foi projetado especificamente para ler um documento que tenha um elemento `Child` de repetição.</span><span class="sxs-lookup"><span data-stu-id="e332c-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="e332c-118">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e332c-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="e332c-119">Nesse exemplo, o documento de origem é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="e332c-119">In this example, the source document is very small.</span></span> <span data-ttu-id="e332c-120">No entanto, mesmo se houver milhões de elementos de `Child` , este exemplo ainda terá uma pegada pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="e332c-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e332c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e332c-121">See also</span></span>
- [<span data-ttu-id="e332c-122">Passo a passo: Implementando IEnumerable(Of T) no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e332c-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [<span data-ttu-id="e332c-123">Analisando XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e332c-123">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
