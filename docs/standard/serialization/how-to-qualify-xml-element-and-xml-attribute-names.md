---
title: Como qualificar elementos XML e nomes de atributos XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 3c477923387e5a28dcc14b44b0f77bb6acb686e5
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46526552"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="f8e6a-102">Como qualificar elementos XML e nomes de atributos XML</span><span class="sxs-lookup"><span data-stu-id="f8e6a-102">How to: Qualify XML Element and XML Attribute Names</span></span>

<span data-ttu-id="f8e6a-103">Namespaces XML contidos por instâncias do <xref:System.Xml.Serialization.XmlSerializerNamespaces> classe deve estar de acordo com a especificação do World Wide Web Consortium (W3C) chamado [Namespaces em XML](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="f8e6a-103">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="f8e6a-104">Os namespaces em XML fornecem um método para qualificar os nomes de elementos XML e atributos XML em documentos XML.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-104">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="f8e6a-105">Um nome qualificado é composto por um prefixo e por um nome local separados por dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-105">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="f8e6a-106">O prefixo funciona somente como espaço reservado; é mapeado para um URI que especifica um namespace.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-106">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="f8e6a-107">A combinação do namespace de URI gerenciado universalmente e o nome local produz um nome que é garantido para ser exclusivo universalmente.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-107">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="f8e6a-108">Ao criar uma instância do `XmlSerializerNamespaces` e adicionar os pares de namespace ao objeto, você pode especificar os prefixos usados em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-108">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="f8e6a-109">Para criar nomes qualificados em um documento XML</span><span class="sxs-lookup"><span data-stu-id="f8e6a-109">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="f8e6a-110">Crie uma instância da classe `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-110">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="f8e6a-111">Adicione todos os prefixos e pares de namespace ao `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-111">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="f8e6a-112">Aplique o atributo `System.Xml.Serialization` apropriado a cada membro ou classe que o <xref:System.Xml.Serialization.XmlSerializer> deve serializar em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-112">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

  <span data-ttu-id="f8e6a-113">Os atributos disponíveis são: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute> e <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-113">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="f8e6a-114">Configure a propriedade `Namespace` de cada atributo para um dos valores de namespace do `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-114">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="f8e6a-115">Passe o `XmlSerializerNamespaces` para o método `Serialize` do `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-115">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="f8e6a-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8e6a-116">Example</span></span>

<span data-ttu-id="f8e6a-117">O exemplo a seguir cria um `XmlSerializerNamespaces` e adiciona dois prefixos e pares de namespace ao objeto.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-117">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="f8e6a-118">O código cria um `XmlSerializer` que é usado para serializar uma instância da classe `Books`.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-118">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="f8e6a-119">O código chama o método `Serialize` com o `XmlSerializerNamespaces`, permitindo que o XML contenha namespaces com prefixo.</span><span class="sxs-lookup"><span data-stu-id="f8e6a-119">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f8e6a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8e6a-120">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="f8e6a-121">A ferramenta de definição de esquema XML e a serialização XML</span><span class="sxs-lookup"><span data-stu-id="f8e6a-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="f8e6a-122">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="f8e6a-122">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="f8e6a-123">Classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="f8e6a-123">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="f8e6a-124">Atributos que controlam a serialização XML</span><span class="sxs-lookup"><span data-stu-id="f8e6a-124">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="f8e6a-125">Como especificar um nome de elemento alternativo para um fluxo XML</span><span class="sxs-lookup"><span data-stu-id="f8e6a-125">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="f8e6a-126">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="f8e6a-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="f8e6a-127">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="f8e6a-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
