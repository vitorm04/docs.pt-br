---
title: Acessando atributos no DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aeb0a8e80a023568f192e832b1e4a3244fc87455
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085115"
---
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="72f3d-102">Acessando atributos no DOM</span><span class="sxs-lookup"><span data-stu-id="72f3d-102">Accessing Attributes in the DOM</span></span>
<span data-ttu-id="72f3d-103">Os atributos são propriedades do elemento, não filhos do elemento.</span><span class="sxs-lookup"><span data-stu-id="72f3d-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="72f3d-104">Essa distinção é importante por causa dos métodos usados para navegar por nós irmãos, pai e filho do DOM (Document Object Model) XML.</span><span class="sxs-lookup"><span data-stu-id="72f3d-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="72f3d-105">Por exemplo, os métodos **PreviousSibling** e **NextSibling** não são usados para navegar de um elemento para um atributo ou entre atributos.</span><span class="sxs-lookup"><span data-stu-id="72f3d-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="72f3d-106">Em vez disso, um atributo é uma propriedade de um elemento e pertence a um elemento, possui uma propriedade **OwnerElement**, não uma propriedade **parentNode**, e possui métodos distintos de navegação.</span><span class="sxs-lookup"><span data-stu-id="72f3d-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>  
  
 <span data-ttu-id="72f3d-107">Quando o nó atual for um elemento, use o método **HasAttribute** para verificar se há algum atributo associado ao elemento.</span><span class="sxs-lookup"><span data-stu-id="72f3d-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="72f3d-108">Quando se sabe que um elemento tem atributos, há vários métodos para acessar atributos.</span><span class="sxs-lookup"><span data-stu-id="72f3d-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="72f3d-109">Para recuperar um único atributo do elemento, use os métodos **GetAttribute** e **GetAttributeNode** do **XmlElement** ou obtenha todos os atributos de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="72f3d-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="72f3d-110">Obter a coleção é útil se você precisar iterar sobre a coleção.</span><span class="sxs-lookup"><span data-stu-id="72f3d-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="72f3d-111">Se desejar todos os atributos do elemento, use a propriedade **Attributes** do elemento para recuperar todos os atributos de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="72f3d-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>  
  
## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="72f3d-112">Recuperando todos os atributos em uma coleção</span><span class="sxs-lookup"><span data-stu-id="72f3d-112">Retrieving All Attributes into a Collection</span></span>  
 <span data-ttu-id="72f3d-113">Se desejar que todos os atributos de um nó do elemento sejam colocados em uma coleção, chame a propriedade **XmlElement.Attributes**.</span><span class="sxs-lookup"><span data-stu-id="72f3d-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="72f3d-114">Isso obtém o **XmlAttributeCollection**, que contém todos os atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="72f3d-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="72f3d-115">A classe **XmlAttributeCollection** herda do mapa **XmlNamedNode**.</span><span class="sxs-lookup"><span data-stu-id="72f3d-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="72f3d-116">Portanto, os métodos e as propriedades disponíveis na coleção incluem os que estão disponíveis em um mapa de nó nomeado além dos métodos e das propriedades específicos à classe **XmlAttributeCollection**, como a propriedade **ItemOf** ou o método **Append**.</span><span class="sxs-lookup"><span data-stu-id="72f3d-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="72f3d-117">Cada item da coleção de atributo representa um nó **XmlAttribute**.</span><span class="sxs-lookup"><span data-stu-id="72f3d-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="72f3d-118">Para localizar o número de atributos em um elemento, obtenha o **XmlAttributeCollection** e use a propriedade **Count** para verificar quantos nós **XmlAttribute** estão na coleção.</span><span class="sxs-lookup"><span data-stu-id="72f3d-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>  
  
 <span data-ttu-id="72f3d-119">O exemplo de código a seguir mostra como recuperar uma coleção de atributos e, usando o método **Count** para o índice de loop, iterar sobre ela.</span><span class="sxs-lookup"><span data-stu-id="72f3d-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="72f3d-120">Em seguida, o código mostra como recuperar um único atributo da coleção e exibir seu valor.</span><span class="sxs-lookup"><span data-stu-id="72f3d-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>  
  
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
  
 <span data-ttu-id="72f3d-121">Esse exemplo exibe a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="72f3d-121">This example displays the following output:</span></span>  
  
 <span data-ttu-id="72f3d-122">**Saída**</span><span class="sxs-lookup"><span data-stu-id="72f3d-122">**Output**</span></span>  
  
 <span data-ttu-id="72f3d-123">Display all the attributes in the collection.</span><span class="sxs-lookup"><span data-stu-id="72f3d-123">Display all the attributes in the collection.</span></span>  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 <span data-ttu-id="72f3d-124">As informações em uma coleção de atributos podem ser recuperadas por nome ou número de índice.</span><span class="sxs-lookup"><span data-stu-id="72f3d-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="72f3d-125">O exemplo acima mostra como recuperar dados por nome.</span><span class="sxs-lookup"><span data-stu-id="72f3d-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="72f3d-126">O próximo exemplo mostra como recuperar dados por número de índice.</span><span class="sxs-lookup"><span data-stu-id="72f3d-126">The next example shows how to retrieve data by index number.</span></span>  
  
 <span data-ttu-id="72f3d-127">Como **XmlAttributeCollection** é uma coleção e pode ser iterada por nome ou índice, este exemplo mostra como selecionar o primeiro atributo da coleção usando um índice com base em zero e usando o seguinte arquivo, **baseuri.xml**, como entrada.</span><span class="sxs-lookup"><span data-stu-id="72f3d-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>  
  
### <a name="input"></a><span data-ttu-id="72f3d-128">Entrada</span><span class="sxs-lookup"><span data-stu-id="72f3d-128">Input</span></span>  
  
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
  
## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="72f3d-129">Recuperando um único nó de atributo</span><span class="sxs-lookup"><span data-stu-id="72f3d-129">Retrieving an Individual Attribute Node</span></span>  
 <span data-ttu-id="72f3d-130">Para recuperar um único nó de atributo de um elemento, o método <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> é usado.</span><span class="sxs-lookup"><span data-stu-id="72f3d-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="72f3d-131">Retorna um objeto do tipo **XmlAttribute**.</span><span class="sxs-lookup"><span data-stu-id="72f3d-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="72f3d-132">Quando você tem um **XmlAttribute**, todos os métodos e propriedades disponíveis na classe <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> estão disponíveis naquele objeto, como localizar o **OwnerElement**.</span><span class="sxs-lookup"><span data-stu-id="72f3d-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>  
  
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
  
 <span data-ttu-id="72f3d-133">Você também pode fazer como mostrado no exemplo anterior, onde um único nó de atributo é recuperado da coleção de atributos.</span><span class="sxs-lookup"><span data-stu-id="72f3d-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="72f3d-134">O exemplo de código a seguir mostra como uma linha de código pode ser escrita para recuperar um único atributo pelo número de índice da raiz da árvore de documentos XML, também conhecida como a propriedade **DocumentElement**.</span><span class="sxs-lookup"><span data-stu-id="72f3d-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a><span data-ttu-id="72f3d-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72f3d-135">See also</span></span>

- [<span data-ttu-id="72f3d-136">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="72f3d-136">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
