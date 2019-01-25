---
title: 'Como: Fragmentos XML de Stream com acesso a informações de cabeçalho (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 26d1d2166aaf8eaa62ba3ef7b3ffa9ab104574e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657318"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="6f660-102">Como: Fragmentos XML de Stream com acesso a informações de cabeçalho (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f660-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="6f660-103">Às vezes você precisará ler arbitrariamente grandes arquivos XML, e escreve seu aplicativo para que os vestígio de memória do aplicativo seja previsível.</span><span class="sxs-lookup"><span data-stu-id="6f660-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="6f660-104">Se você tentar preencher uma árvore XML com um grande arquivo XML, seu uso de memória será proporcionalmente o tamanho do arquivo que é, excessivo.</span><span class="sxs-lookup"><span data-stu-id="6f660-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="6f660-105">Portanto, você deve usar uma técnica de streaming em vez disso.</span><span class="sxs-lookup"><span data-stu-id="6f660-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="6f660-106">Uma opção é escrever seu aplicativo usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="6f660-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="6f660-107">No entanto, talvez você queira usar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para consultar a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="6f660-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="6f660-108">Se esse for o caso, você pode escrever seu próprio método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="6f660-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="6f660-109">Para obter mais informações, confira [Como: Gravar um LINQ para o método de eixo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="6f660-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="6f660-110">Para escrever seu próprio método do eixo, você escreve um pequeno método que usa <xref:System.Xml.XmlReader> para ler nós até que atingiu um dos nós em que você está interessado.</span><span class="sxs-lookup"><span data-stu-id="6f660-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="6f660-111">O método chama em <xref:System.Xml.Linq.XNode.ReadFrom%2A>, que lê de <xref:System.Xml.XmlReader> e cria uma instância de um fragmento XML.</span><span class="sxs-lookup"><span data-stu-id="6f660-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="6f660-112">Você pode escrever consultas LINQ no método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="6f660-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="6f660-113">As técnicas de streaming são melhor aplicadas em situações onde você precisa processar o documento de origem apenas uma vez e você pode processar os elementos na ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="6f660-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="6f660-114">Determinados operadores de consulta padrão, como <xref:System.Linq.Enumerable.OrderBy%2A>, iteram sua origem, coletam todos os dados, classificam e, em seguida, geram finalmente o primeiro item na sequência.</span><span class="sxs-lookup"><span data-stu-id="6f660-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="6f660-115">Observe que se você usar um operador de consulta que materialize sua origem antes de como o primeiro item, você não manterá pegada uma pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="6f660-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f660-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f660-116">Example</span></span>  
 <span data-ttu-id="6f660-117">Às vezes o problema é apenas um pouco mais interessante.</span><span class="sxs-lookup"><span data-stu-id="6f660-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="6f660-118">No documento XML a seguir, o consumidor do método personalizado do eixo também precisa saber o nome do cliente que cada item pertence.</span><span class="sxs-lookup"><span data-stu-id="6f660-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="6f660-119">A abordagem que este exemplo usa é inspecione também para essas informações de cabeçalho, salvar informações de cabeçalho, e então cria uma árvore XML pequena que contém informações de cabeçalho e o detalhe que você está enumerando.</span><span class="sxs-lookup"><span data-stu-id="6f660-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="6f660-120">O método do eixo resulta nessa nova árvore, pequena XML.</span><span class="sxs-lookup"><span data-stu-id="6f660-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="6f660-121">A consulta possui o acesso a informações de cabeçalho bem como para informações detalhadas.</span><span class="sxs-lookup"><span data-stu-id="6f660-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="6f660-122">Essa abordagem tem uma pegada pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="6f660-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="6f660-123">Como cada fragmento XML de detalhe é rendido, nenhuma referência é mantido para o fragmento anterior, e está disponível para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6f660-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="6f660-124">Observe que essa técnica cria uma breve muitos objetos na heap.</span><span class="sxs-lookup"><span data-stu-id="6f660-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="6f660-125">O exemplo a seguir mostra como implementar e usar um método personalizado do eixo que passa fragmentos XML do arquivo especificado por um URI.</span><span class="sxs-lookup"><span data-stu-id="6f660-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="6f660-126">Esse eixo personalizado é escrito especificamente para que espera um documento que tem `Customer`, `Name`, e os elementos de `Item` , e que esses elementos serão organizados como no documento anterior de `Source.xml` .</span><span class="sxs-lookup"><span data-stu-id="6f660-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="6f660-127">É uma implementação simplista.</span><span class="sxs-lookup"><span data-stu-id="6f660-127">It is a simplistic implementation.</span></span> <span data-ttu-id="6f660-128">Uma implementação mais robusta seria preparada para analisar um documento válido.</span><span class="sxs-lookup"><span data-stu-id="6f660-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="6f660-129">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="6f660-129">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f660-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f660-130">See also</span></span>
- [<span data-ttu-id="6f660-131">LINQ to XML (Visual Basic) de programação avançada</span><span class="sxs-lookup"><span data-stu-id="6f660-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
