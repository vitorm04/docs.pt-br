---
title: "Como: transmitir fragmentos XML com acesso a informa&#231;&#245;es de cabe&#231;alho (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: transmitir fragmentos XML com acesso a informa&#231;&#245;es de cabe&#231;alho (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Às vezes você precisa ler arbitrariamente grandes arquivos XML e escrever seu aplicativo para que a superfície de memória do aplicativo é previsível. Se você tentar preencher uma árvore XML com um arquivo XML grande, seu uso de memória será proporcional ao tamanho do arquivo — isto é, excessivo. Portanto, você deve usar uma técnica de streaming.  
  
 Uma opção é escrever seu aplicativo usando <xref:System.Xml.XmlReader>. No entanto, você talvez queira usar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para consultar a árvore XML. Se esse for o caso, você pode escrever seu próprio método personalizado do eixo. Para obter mais informações, consulte [How to: Write a LINQ to XML Axis Method \(Visual Basic\)](../Topic/How%20to:%20Write%20a%20LINQ%20to%20XML%20Axis%20Method%20\(Visual%20Basic\).md).  
  
 Para escrever seu próprio método de eixo, você escreve um método pequeno que usa o <xref:System.Xml.XmlReader> para ler nós até atingir um de nós no qual você está interessado. Em seguida, chama o método <xref:System.Xml.Linq.XNode.ReadFrom%2A>, que lê a partir do <xref:System.Xml.XmlReader> e instancia um fragmento XML. Em seguida, você pode escrever consultas LINQ no método personalizado do eixo.  
  
 As técnicas de streaming são melhor aplicadas em situações em que você precisa processar o documento de origem apenas uma vez, e você pode processar os elementos na ordem do documento. Determinados operadores de consulta padrão, como <xref:System.Linq.Enumerable.OrderBy%2A>, iteram sua origem, coletar todos os dados, classificá\-los e, em seguida, geram finalmente o primeiro item na sequência. Observe que se você usar um operador de consulta que materializa sua origem antes de gerar o primeiro item, você não manterá uma pegada pequena de memória.  
  
## Exemplo  
 Às vezes, o problema fica um pouco mais interessante. No seguinte documento XML, o consumidor do método personalizado do eixo também precisa saber o nome do cliente que cada item pertence.  
  
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
  
 A abordagem que este exemplo usa é Inspecione também para essas informações de cabeçalho, salvar as informações de cabeçalho e, em seguida, criar uma árvore XML pequena que contém as informações de cabeçalho e os detalhes que você está enumerando. O método do eixo resulta nessa árvore XML pequeno. A consulta, em seguida, tem acesso a informações de cabeçalho, bem como as informações detalhadas.  
  
 Essa abordagem tem uma pegada pequena de memória. Como cada fragmento XML de detalhe é rendido, nenhuma referência é mantido para o fragmento anterior, e está disponível para coleta de lixo. Observe que essa técnica cria uma breve muitos objetos no heap.  
  
 O exemplo a seguir mostra como implementar e usar um método personalizado do eixo que passa fragmentos XML do arquivo especificado pelo URI. Esse eixo personalizado é escrito especificamente para que ele espera um documento que tem `Customer`, `Name`, e `Item` elementos, e que esses elementos serão organizados como acima `Source.xml` documento. É uma implementação simples. Uma implementação mais robusta seria preparada para analisar um documento inválido.  
  
```vb#  
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
  
 Esse código produz a seguinte saída:  
  
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
  
## Consulte também  
 [Advanced LINQ to XML Programming \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)