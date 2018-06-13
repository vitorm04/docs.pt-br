---
title: A pré-compilação Atomização de XName objetos (LINQ para XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 141aa5e19e75e4a09b2d7aa04d83e8a24d2a27f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645714"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>A pré-compilação Atomização de XName objetos (LINQ para XML) (Visual Basic)
Uma maneira para melhorar o desempenho em LINQ to XML é pré-compilação atomizar objetos de <xref:System.Xml.Linq.XName> . a pré-compilação atomização significa que você atribuir uma cadeia de caracteres a um objeto de <xref:System.Xml.Linq.XName> antes de criar a árvore XML usando os construtores de classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XAttribute> . Em seguida, em vez de passar uma cadeia de caracteres para o construtor, que usaria a conversão implícita de cadeia de caracteres a <xref:System.Xml.Linq.XName>, você passa o objeto inicializado de <xref:System.Xml.Linq.XName> .  
  
 Isso melhora o desempenho quando você cria uma grande árvore XML em que os nomes específicos são repetidos. Para fazer isso, você declarar e inicializar objetos de <xref:System.Xml.Linq.XName> antes que você construa a árvore XML e em seguida, usar objetos de <xref:System.Xml.Linq.XName> em vez de especificar cadeias de caracteres para nomes de elementos e atributos. Essa técnica pode produzir ganhos significativos de desempenho se você estiver criando um grande número de elementos ou atributos () com o mesmo nome.  
  
 Você deve testar a pré-compilação atomização com seu cenário para decidir se você usar o.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra isso.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 O exemplo a seguir mostra a mesma técnica onde o documento XML é em um namespace:  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 O exemplo a seguir é mais semelhante ao que você provavelmente encontrará no mundo real. Nesse exemplo, o conteúdo do elemento é fornecido por uma consulta:  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 O exemplo anterior executa melhor do que o exemplo, em que os nomes não são atomizados passos:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Desempenho (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [Atomizado XName e XNamespace objeto (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
