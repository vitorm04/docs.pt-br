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
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="26dc9-102">Acessando atributos no DOM</span><span class="sxs-lookup"><span data-stu-id="26dc9-102">Accessing Attributes in the DOM</span></span>
<span data-ttu-id="26dc9-103">Os atributos são propriedades do elemento, não filhos do elemento.</span><span class="sxs-lookup"><span data-stu-id="26dc9-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="26dc9-104">Essa distinção é importante por causa dos métodos usados para navegar por nós irmãos, pai e filho do DOM (Document Object Model) XML.</span><span class="sxs-lookup"><span data-stu-id="26dc9-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="26dc9-105">Por exemplo, o **PreviousSibling** e **NextSibling** métodos não são usados para navegar de um elemento para um atributo ou entre atributos.</span><span class="sxs-lookup"><span data-stu-id="26dc9-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="26dc9-106">Em vez disso, um atributo é uma propriedade de um elemento e pertence a um elemento, tem um **OwnerElement** propriedade e não um **parentNode** propriedade, e tem diferentes métodos de navegação.</span><span class="sxs-lookup"><span data-stu-id="26dc9-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>  
  
 <span data-ttu-id="26dc9-107">Quando o nó atual é um elemento, use o **HasAttribute** método para verificar se há qualquer atributo associado ao elemento.</span><span class="sxs-lookup"><span data-stu-id="26dc9-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="26dc9-108">Quando se sabe que um elemento tem atributos, há vários métodos para acessar atributos.</span><span class="sxs-lookup"><span data-stu-id="26dc9-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="26dc9-109">Para recuperar um único atributo do elemento, você pode usar o **GetAttribute** e **GetAttributeNode** métodos do **XmlElement** ou você pode obter todos os atributos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="26dc9-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="26dc9-110">Obter a coleção é útil se você precisar iterar sobre a coleção.</span><span class="sxs-lookup"><span data-stu-id="26dc9-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="26dc9-111">Se desejar que todos os atributos do elemento, use o **atributos** propriedade do elemento para recuperar todos os atributos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="26dc9-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>  
  
## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="26dc9-112">Recuperando todos os atributos em uma coleção</span><span class="sxs-lookup"><span data-stu-id="26dc9-112">Retrieving All Attributes into a Collection</span></span>  
 <span data-ttu-id="26dc9-113">Se desejar que todos os atributos de um nó de elemento coloque em uma coleção, chame o **XmlElement.Attributes** propriedade.</span><span class="sxs-lookup"><span data-stu-id="26dc9-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="26dc9-114">Obtém o **XmlAttributeCollection** que contém todos os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="26dc9-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="26dc9-115">O **XmlAttributeCollection** classe herda o **XmlNamedNode** mapa.</span><span class="sxs-lookup"><span data-stu-id="26dc9-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="26dc9-116">Portanto, os métodos e propriedades disponíveis na coleção de incluem-los disponíveis em um mapa de nó nomeado além de métodos e propriedades específicas para o **XmlAttributeCollection** classe, como o **ItemOf**  propriedade ou o **Append** método.</span><span class="sxs-lookup"><span data-stu-id="26dc9-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="26dc9-117">Cada item na coleção de atributos representa um **XmlAttribute** nó.</span><span class="sxs-lookup"><span data-stu-id="26dc9-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="26dc9-118">Para localizar o número de atributos em um elemento, obter o **XmlAttributeCollection**e usar o **contagem** propriedade para ver quantos **XmlAttribute** nós estão na coleção.</span><span class="sxs-lookup"><span data-stu-id="26dc9-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>  
  
 <span data-ttu-id="26dc9-119">O exemplo de código a seguir mostra como recuperar um atributo de coleção e, usando o **contagem** método para o índice de loop, a iterar.</span><span class="sxs-lookup"><span data-stu-id="26dc9-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="26dc9-120">Em seguida, o código mostra como recuperar um único atributo da coleção e exibir seu valor.</span><span class="sxs-lookup"><span data-stu-id="26dc9-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>  
  
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
  
 <span data-ttu-id="26dc9-121">Esse exemplo exibe a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="26dc9-121">This example displays the following output:</span></span>  
  
 <span data-ttu-id="26dc9-122">**Saída**</span><span class="sxs-lookup"><span data-stu-id="26dc9-122">**Output**</span></span>  
  
 <span data-ttu-id="26dc9-123">Display all the attributes in the collection.</span><span class="sxs-lookup"><span data-stu-id="26dc9-123">Display all the attributes in the collection.</span></span>  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 <span data-ttu-id="26dc9-124">As informações em uma coleção de atributos podem ser recuperadas por nome ou número de índice.</span><span class="sxs-lookup"><span data-stu-id="26dc9-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="26dc9-125">O exemplo acima mostra como recuperar dados por nome.</span><span class="sxs-lookup"><span data-stu-id="26dc9-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="26dc9-126">O próximo exemplo mostra como recuperar dados por número de índice.</span><span class="sxs-lookup"><span data-stu-id="26dc9-126">The next example shows how to retrieve data by index number.</span></span>  
  
 <span data-ttu-id="26dc9-127">Porque o **XmlAttributeCollection** é uma coleção e pode ser iterado por nome ou índice, este exemplo mostra o primeiro atributo fora da coleção usando um índice com base em zero e o arquivo a seguir, a seleção **baseuri.xml**, como entrada.</span><span class="sxs-lookup"><span data-stu-id="26dc9-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>  
  
### <a name="input"></a><span data-ttu-id="26dc9-128">Entrada</span><span class="sxs-lookup"><span data-stu-id="26dc9-128">Input</span></span>  
  
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
  
## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="26dc9-129">Recuperando um único nó de atributo</span><span class="sxs-lookup"><span data-stu-id="26dc9-129">Retrieving an Individual Attribute Node</span></span>  
 <span data-ttu-id="26dc9-130">Para recuperar um único nó de atributo de um elemento, o método <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> é usado.</span><span class="sxs-lookup"><span data-stu-id="26dc9-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="26dc9-131">Retorna um objeto do tipo **XmlAttribute**.</span><span class="sxs-lookup"><span data-stu-id="26dc9-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="26dc9-132">Depois que você tiver um **XmlAttribute**, todos os métodos e propriedades disponíveis no <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> classe estão disponíveis no objeto, como encontrar o **OwnerElement**.</span><span class="sxs-lookup"><span data-stu-id="26dc9-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>  
  
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
  
 <span data-ttu-id="26dc9-133">Você também pode fazer como mostrado no exemplo anterior, onde um único nó de atributo é recuperado da coleção de atributos.</span><span class="sxs-lookup"><span data-stu-id="26dc9-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="26dc9-134">O exemplo a seguir mostra como uma linha de código pode ser gravada para recuperar um único atributo pelo número de índice da raiz do documento XML de árvore, também conhecido como o **DocumentElement** propriedade.</span><span class="sxs-lookup"><span data-stu-id="26dc9-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a><span data-ttu-id="26dc9-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26dc9-135">See Also</span></span>  
 [<span data-ttu-id="26dc9-136">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="26dc9-136">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
