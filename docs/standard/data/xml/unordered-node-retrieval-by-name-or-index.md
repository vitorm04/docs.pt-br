---
title: Recuperação não ordenada do nó por nome ou índice
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 785a609455a35dd87a9593f00b58fd160ac708e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572935"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="4a9d3-102">Recuperação não ordenada do nó por nome ou índice</span><span class="sxs-lookup"><span data-stu-id="4a9d3-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="4a9d3-103">**XmlNamedNodeMap** é descrito na especificação do W3C (World Wide Web Consortium) como NamedNodeMap e é necessário para tratar um conjunto não ordenado de nós com a capacidade de fazer referência a nós pelos respectivos nome ou índice.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="4a9d3-104">A única maneira de ter acesso a um **XmlNamedNodeMap** é quando um **XmlNamedNodeMap** é retornado através de um método ou de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="4a9d3-105">Há três métodos ou propriedades que retornam um **XmlNamedNodeMap**:</span><span class="sxs-lookup"><span data-stu-id="4a9d3-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
-   <span data-ttu-id="4a9d3-106">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="4a9d3-106">XmlElement.Attributes</span></span>  
  
-   <span data-ttu-id="4a9d3-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="4a9d3-107">XmlDocumentType.Entities</span></span>  
  
-   <span data-ttu-id="4a9d3-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="4a9d3-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="4a9d3-109">Por exemplo, a propriedade **XmlDocumentType.Entities** obtém a coleção de nós de **XmlEntity** declarados na declaração de tipo de documento.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="4a9d3-110">Essa coleção é retornada como **XmlNamedNodeMap**, e você pode fazer iterações através da coleção, usando a propriedade **Count** e as informações da entidade de exibição.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="4a9d3-111">Para ver um exemplo de iteração através de um **XmlNamedNodeMap**, confira <xref:System.Xml.XmlDocumentType.Entities%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="4a9d3-112">**XmlAttributeCollection** é derivado de **XmlNamedNodeMap** e apenas os atributos são modificáveis, ao passo que as anotações e entidades são destinadas a somente leitura.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="4a9d3-113">Quando usa **XmlNamedNodeMap** nos atributos, você pode obter nós para esses atributos com base nos respectivos nomes XML.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="4a9d3-114">Isso fornece um método fácil para manipular a coleção de atributos em um nó de elemento.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="4a9d3-115">Isso pode ser comparado diretamente com **XmlNodeList**, que também implementa a interface de **IEnumerable**, mas com um acessador de índice em vez de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="4a9d3-116">Os métodos **RemoveNamedItem** e **SetNamedItem** são usados somente em **XmlAttributeCollection**.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="4a9d3-117">Ao adicionar ou remover de uma coleção de atributos usando a implementação de **AttributeCollection** ou **XmlNamedNodeMap** modificará a coleção de atributos no elemento.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="4a9d3-118">O exemplo de código a seguir mostra como mover um atributo e criar um novo atributo.</span><span class="sxs-lookup"><span data-stu-id="4a9d3-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );           
  
    }  
}  
```  
  
 <span data-ttu-id="4a9d3-119">Para ver um exemplo de código adicional que mostra um atributo que está sendo removido de **AttributeCollection**, confira o [Método XmlNamedNodeMap.RemoveNamedItem](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span><span class="sxs-lookup"><span data-stu-id="4a9d3-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span></span> <span data-ttu-id="4a9d3-120">Para saber mais sobre métodos e propriedades, confira [Membros XmlNamedNodeMap](AllMembers.T:System.Xml.XmlNamedNodeMap).</span><span class="sxs-lookup"><span data-stu-id="4a9d3-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](AllMembers.T:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a9d3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a9d3-121">See Also</span></span>  
 [<span data-ttu-id="4a9d3-122">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="4a9d3-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
