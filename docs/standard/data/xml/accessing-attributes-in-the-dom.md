---
title: Acessando atributos no DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a433ec5f83a50aa4fe4b2017a0dac3d2a5e5710c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-attributes-in-the-dom"></a>Acessando atributos no DOM
Os atributos são propriedades do elemento, não filhos do elemento. Essa distinção é importante por causa dos métodos usados para navegar por nós irmãos, pai e filho do DOM (Document Object Model) XML. Por exemplo, o **PreviousSibling** e **NextSibling** métodos não são usados para navegar de um elemento para um atributo ou entre atributos. Em vez disso, um atributo é uma propriedade de um elemento e pertence a um elemento, tem um **OwnerElement** propriedade e não um **parentNode** propriedade, e tem diferentes métodos de navegação.  
  
 Quando o nó atual é um elemento, use o **HasAttribute** método para verificar se há qualquer atributo associado ao elemento. Quando se sabe que um elemento tem atributos, há vários métodos para acessar atributos. Para recuperar um único atributo do elemento, você pode usar o **GetAttribute** e **GetAttributeNode** métodos do **XmlElement** ou você pode obter todos os atributos em uma coleção. Obter a coleção é útil se você precisar iterar sobre a coleção. Se desejar que todos os atributos do elemento, use o **atributos** propriedade do elemento para recuperar todos os atributos em uma coleção.  
  
## <a name="retrieving-all-attributes-into-a-collection"></a>Recuperando todos os atributos em uma coleção  
 Se desejar que todos os atributos de um nó de elemento coloque em uma coleção, chame o **XmlElement.Attributes** propriedade. Obtém o **XmlAttributeCollection** que contém todos os atributos de um elemento. O **XmlAttributeCollection** classe herda o **XmlNamedNode** mapa. Portanto, os métodos e propriedades disponíveis na coleção de incluem-los disponíveis em um mapa de nó nomeado além de métodos e propriedades específicas para o **XmlAttributeCollection** classe, como o **ItemOf**  propriedade ou o **Append** método. Cada item na coleção de atributos representa um **XmlAttribute** nó. Para localizar o número de atributos em um elemento, obter o **XmlAttributeCollection**e usar o **contagem** propriedade para ver quantos **XmlAttribute** nós estão na coleção.  
  
 O exemplo de código a seguir mostra como recuperar um atributo de coleção e, usando o **contagem** método para o índice de loop, a iterar. Em seguida, o código mostra como recuperar um único atributo da coleção e exibir seu valor.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.   
        Dim myElement As XmlElement = doc.DocumentElement  
  
        ' Create an attribute collection from the element.  
        Dim attrColl As XmlAttributeCollection = myElement.Attributes  
  
        ' Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...")  
        Dim i As Integer  
        For i = 0 To attrColl.Count - 1  
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)  
            Console.Write("{0}", attrColl.ItemOf(i).Value)  
            Console.WriteLine()  
        Next  
  
        ' Retrieve a single attribute from the collection; specifically, the  
        ' attribute with the name "misc".  
        Dim attr As XmlAttribute = attrColl("misc")  
  
        ' Retrieve the value from that attribute.  
        Dim miscValue As String = attr.InnerXml  
  
        Console.WriteLine("Display the attribute information.")  
        Console.WriteLine(miscValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  
    public static void Main()  
    {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +  
                      "<title>The Handmaid's Tale</title>" +  
                      "<price>14.95</price>" +  
                      "</book>");  
  
        // Move to an element.  
        XmlElement myElement = doc.DocumentElement;  
  
        // Create an attribute collection from the element.  
        XmlAttributeCollection attrColl = myElement.Attributes;  
  
        // Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...");  
        for (int i = 0; i < attrColl.Count; i++)  
        {  
            Console.Write("{0} = ", attrColl[i].Name);  
            Console.Write("{0}", attrColl[i].Value);  
            Console.WriteLine();  
        }  
  
        // Retrieve a single attribute from the collection; specifically, the  
        // attribute with the name "misc".  
        XmlAttribute attr = attrColl["misc"];  
  
        // Retrieve the value from that attribute.  
        String miscValue = attr.InnerXml;  
  
        Console.WriteLine("Display the attribute information.");  
        Console.WriteLine(miscValue);  
  
    }  
}  
```  
  
 Esse exemplo exibe a seguinte saída:  
  
 **Saída**  
  
 Display all the attributes in the collection.  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 As informações em uma coleção de atributos podem ser recuperadas por nome ou número de índice. O exemplo acima mostra como recuperar dados por nome. O próximo exemplo mostra como recuperar dados por número de índice.  
  
 Porque o **XmlAttributeCollection** é uma coleção e pode ser iterado por nome ou índice, este exemplo mostra o primeiro atributo fora da coleção usando um índice com base em zero e o arquivo a seguir, a seleção **baseuri.xml**, como entrada.  
  
### <a name="input"></a>Entrada  
  
```xml  
<!-- XML fragment -->  
<book genre="novel">  
  <title>Pride And Prejudice</title>  
</book>  
```  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.Load("http://localhost/baseuri.xml")  
  
        ' Display information on the attribute node. The value  
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.  
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)  
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)  
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)  
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
    End Sub 'Main   
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    // Create the XmlDocument.  
    XmlDocument doc = new XmlDocument();  
  
    doc.Load("http://localhost/baseuri.xml");  
  
    // Display information on the attribute node. The value  
    // returned for BaseURI is 'http://localhost/baseuri.xml'.  
    XmlAttribute attr = doc.DocumentElement.Attributes[0];  
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);  
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);  
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## <a name="retrieving-an-individual-attribute-node"></a>Recuperando um único nó de atributo  
 Para recuperar um único nó de atributo de um elemento, o método <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> é usado. Retorna um objeto do tipo **XmlAttribute**. Depois que você tiver um **XmlAttribute**, todos os métodos e propriedades disponíveis no <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> classe estão disponíveis no objeto, como encontrar o **OwnerElement**.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.  
        Dim root As XmlElement  
        root = doc.DocumentElement  
  
        ' Get an attribute.  
        Dim attr As XmlAttribute  
        attr = root.GetAttributeNode("ISBN")  
  
        ' Display the value of the attribute.  
        Dim attrValue As String  
        attrValue = attr.InnerXml  
        Console.WriteLine(attrValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
 public class Sample  
 {  
      public static void Main()  
      {  
    XmlDocument doc = new XmlDocument();  
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +  
                   "<title>The Handmaid's Tale</title>" +  
                   "<price>14.95</price>" +  
                   "</book>");   
  
    // Move to an element.  
     XmlElement root = doc.DocumentElement;  
  
    // Get an attribute.  
     XmlAttribute attr = root.GetAttributeNode("ISBN");  
  
    // Display the value of the attribute.  
     String attrValue = attr.InnerXml;  
     Console.WriteLine(attrValue);  
  
    }  
}  
```  
  
 Você também pode fazer como mostrado no exemplo anterior, onde um único nó de atributo é recuperado da coleção de atributos. O exemplo a seguir mostra como uma linha de código pode ser gravada para recuperar um único atributo pelo número de índice da raiz do documento XML de árvore, também conhecido como o **DocumentElement** propriedade.  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
