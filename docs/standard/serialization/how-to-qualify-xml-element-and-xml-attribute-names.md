---
title: Como qualificar elementos XML e nomes de atributos XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 048bcc587915467f644a2cce695cec352147223a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="b0d5a-102">Como qualificar elementos XML e nomes de atributos XML</span><span class="sxs-lookup"><span data-stu-id="b0d5a-102">How to: Qualify XML Element and XML Attribute Names</span></span>
[<span data-ttu-id="b0d5a-103">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="b0d5a-103">Code Example</span></span>](#cpconworkingwithxmlnamespacesanchor1)  
  
 <span data-ttu-id="b0d5a-104">Os namespaces XML contidos por instâncias da classe <xref:System.Xml.Serialization.XmlSerializerNamespaces> devem estar em conformidade com a especificação do World Wide Web Consortium (www.w3.org) chamada "Namespaces em XML."</span><span class="sxs-lookup"><span data-stu-id="b0d5a-104">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (www.w3.org) specification called "Namespaces in XML."</span></span>  
  
 <span data-ttu-id="b0d5a-105">Os namespaces em XML fornecem um método para qualificar os nomes de elementos XML e atributos XML em documentos XML.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-105">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="b0d5a-106">Um nome qualificado é composto por um prefixo e por um nome local separados por dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-106">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="b0d5a-107">O prefixo funciona somente como espaço reservado; é mapeado para um URI que especifica um namespace.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-107">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="b0d5a-108">A combinação do namespace de URI gerenciado universalmente e o nome local produz um nome que é garantido para ser exclusivo universalmente.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-108">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>  
  
 <span data-ttu-id="b0d5a-109">Ao criar uma instância do `XmlSerializerNamespaces` e adicionar os pares de namespace ao objeto, você pode especificar os prefixos usados em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-109">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>  
  
### <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="b0d5a-110">Para criar nomes qualificados em um documento XML</span><span class="sxs-lookup"><span data-stu-id="b0d5a-110">To create qualified names in an XML document</span></span>  
  
1.  <span data-ttu-id="b0d5a-111">Crie uma instância da classe `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-111">Create an instance of the `XmlSerializerNamespaces` class.</span></span>  
  
2.  <span data-ttu-id="b0d5a-112">Adicione todos os prefixos e pares de namespace ao `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-112">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>  
  
3.  <span data-ttu-id="b0d5a-113">Aplique o atributo `System.Xml.Serialization` apropriado a cada membro ou classe que o <xref:System.Xml.Serialization.XmlSerializer> deve serializar em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-113">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>  
  
     <span data-ttu-id="b0d5a-114">Os atributos disponíveis são: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute> e <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-114">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>  
  
4.  <span data-ttu-id="b0d5a-115">Configure a propriedade `Namespace` de cada atributo para um dos valores de namespace do `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-115">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>  
  
5.  <span data-ttu-id="b0d5a-116">Passe o `XmlSerializerNamespaces` para o método `Serialize` do `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-116">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0d5a-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0d5a-117">Example</span></span>  
 <span data-ttu-id="b0d5a-118">O exemplo a seguir cria um `XmlSerializerNamespaces` e adiciona dois prefixos e pares de namespace ao objeto.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-118">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="b0d5a-119">O código cria um `XmlSerializer` que é usado para serializar uma instância da classe `Books`.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-119">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="b0d5a-120">O código chama o método `Serialize` com o `XmlSerializerNamespaces`, permitindo que o XML contenha namespaces com prefixo.</span><span class="sxs-lookup"><span data-stu-id="b0d5a-120">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>  
  
```vb  
Option Explicit   
public class Price  
{  
    [XmlAttribute(Namespace = "http://www.cpandl.com")]  
    public string currency;  
    [XmlElement(Namespace = "http://www.cohowinery.com")]  
    public decimal price;  
}  
  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Serialization  
  
Public Class Run  
  
    Public Shared Sub Main()  
        Dim test As New Run()  
        test.SerializeObject("XmlNamespaces.xml")  
    End Sub 'Main  
  
    Public Sub SerializeObject(filename As String)  
        Dim mySerializer As New XmlSerializer(GetType(Books))  
        ' Writing a file requires a TextWriter.  
        Dim myWriter As New StreamWriter(filename)  
  
        ' Creates an XmlSerializerNamespaces and adds two  
        ' prefix-namespace pairs.   
        Dim myNamespaces As New XmlSerializerNamespaces()  
        myNamespaces.Add("books", "http://www.cpandl.com")  
        myNamespaces.Add("money", "http://www.cohowinery.com")  
  
        ' Creates a Book.  
        Dim myBook As New Book()  
        myBook.TITLE = "A Book Title"  
        Dim myPrice As New Price()  
        myPrice.price = CDec(9.95)  
        myPrice.currency = "US Dollar"  
        myBook.PRICE = myPrice  
        Dim myBooks As New Books()  
        myBooks.Book = myBook  
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)  
        myWriter.Close()  
    End Sub  
End Class  
  
Public Class Books  
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
    Public Book As Book  
End Class 'Books  
  
<XmlType([Namespace] := "http://www.cpandl.com")> _  
Public Class Book  
  
    <XmlElement([Namespace] := "http://www.cpandl.com")> _  
    Public TITLE As String  
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
    Public PRICE As Price  
End Class  
  
Public Class Price  
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _  
    Public currency As String  
    Public <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
        price As Decimal  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Serialization;  
  
public class Run  
{  
    public static void Main()  
    {  
        Run test = new Run();  
        test.SerializeObject("XmlNamespaces.xml");  
    }  
    public void SerializeObject(string filename)  
    {  
        XmlSerializer mySerializer = new XmlSerializer(typeof(Books));  
        // Writing a file requires a TextWriter.  
        TextWriter myWriter = new StreamWriter(filename);  
  
        // Creates an XmlSerializerNamespaces and adds two  
        // prefix-namespace pairs.  
        XmlSerializerNamespaces myNamespaces =   
        new XmlSerializerNamespaces();  
        myNamespaces.Add("books", "http://www.cpandl.com");  
        myNamespaces.Add("money", "http://www.cohowinery.com");  
  
        // Creates a Book.  
        Book myBook = new Book();  
        myBook.TITLE = "A Book Title";  
        Price myPrice = new Price();  
        myPrice.price = (decimal) 9.95;  
        myPrice.currency = "US Dollar";  
        myBook.PRICE = myPrice;  
        Books myBooks = new Books();  
        myBooks.Book = myBook;  
        mySerializer.Serialize(myWriter,myBooks,myNamespaces);  
        myWriter.Close();  
    }  
}  
  
public class Books  
{  
    [XmlElement(Namespace = "http://www.cohowinery.com")]  
    public Book Book;  
}  
  
[XmlType(Namespace ="http://www.cpandl.com")]  
public class Book  
{  
    [XmlElement(Namespace = "http://www.cpandl.com")]  
    public string TITLE;  
    [XmlElement(Namespace ="http://www.cohowinery.com")]  
    public Price PRICE;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0d5a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0d5a-121">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="b0d5a-122">A ferramenta de definição de esquema XML e a serialização XML</span><span class="sxs-lookup"><span data-stu-id="b0d5a-122">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 [<span data-ttu-id="b0d5a-123">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="b0d5a-123">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="b0d5a-124">Classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="b0d5a-124">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)  
 [<span data-ttu-id="b0d5a-125">Atributos que controlam a serialização XML</span><span class="sxs-lookup"><span data-stu-id="b0d5a-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 [<span data-ttu-id="b0d5a-126">Como especificar um nome de elemento alternativo para um fluxo XML</span><span class="sxs-lookup"><span data-stu-id="b0d5a-126">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [<span data-ttu-id="b0d5a-127">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="b0d5a-127">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="b0d5a-128">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="b0d5a-128">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
