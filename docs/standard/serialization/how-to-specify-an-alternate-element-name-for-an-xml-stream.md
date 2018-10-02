---
title: Como especificar um nome de elemento alternativo para um fluxo XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
ms.openlocfilehash: 8cb6a66f9fc7a67ae99574e783fd889537b9b11a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034487"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a><span data-ttu-id="d0aeb-102">Como especificar um nome de elemento alternativo para um fluxo XML</span><span class="sxs-lookup"><span data-stu-id="d0aeb-102">How to: Specify an Alternate Element Name for an XML Stream</span></span>
[<span data-ttu-id="d0aeb-103">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="d0aeb-103">Code Example</span></span>](#cpconoverridingserializationofclasseswithxmlattributeoverridesclassanchor1)  
  
 <span data-ttu-id="d0aeb-104">Usando o [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), você pode gerar mais de um fluxo XML com o mesmo conjunto de classes.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-104">Using the [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), you can generate more than one XML stream with the same set of classes.</span></span> <span data-ttu-id="d0aeb-105">Você deve querer fazer isso porque dois diferentes serviços Web XML exigem as mesmas informações básicas, com apenas poucas diferenças.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-105">You might want to do this because two different XML Web services require the same basic information, with only slight differences.</span></span> <span data-ttu-id="d0aeb-106">Por exemplo, imagine dois serviços Web XML que processam pedidos para livros e, portanto, exigem números ISBN.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-106">For example, imagine two XML Web services that process orders for books, and thus both require ISBN numbers.</span></span> <span data-ttu-id="d0aeb-107">Um serviço usa a marca \<ISBN>, enquanto o segundo usa a marca \<BookID>.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-107">One service uses the tag \<ISBN> while the second uses the tag \<BookID>.</span></span> <span data-ttu-id="d0aeb-108">Você tem uma classe nomeada `Book` que contém um campo nomeado `ISBN`.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-108">You have a class named `Book` that contains a field named `ISBN`.</span></span> <span data-ttu-id="d0aeb-109">Quando uma instância da classe `Book` é serializada, ela, por padrão, usará o nome de membro (ISBN) como o nome de elemento da marca.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-109">When an instance of the `Book` class is serialized, it will, by default, use the member name (ISBN) as the tag element name.</span></span> <span data-ttu-id="d0aeb-110">Para o primeiro serviço Web XML, esse é o esperado.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-110">For the first XML Web service, this is as expected.</span></span> <span data-ttu-id="d0aeb-111">Mas, para enviar o fluxo XML para o segundo serviço Web XML, você deverá sobrescrever a serialização para que o nome do elemento da marca seja `BookID`.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-111">But to send the XML stream to the second XML Web service, you must override the serialization so that the tag's element name is `BookID`.</span></span>  
  
### <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a><span data-ttu-id="d0aeb-112">Para criar um fluxo XML com um nome de elemento alternativo</span><span class="sxs-lookup"><span data-stu-id="d0aeb-112">To create an XML stream with an alternate element name</span></span>  
  
1.  <span data-ttu-id="d0aeb-113">Crie uma instância da classe <xref:System.Xml.Serialization.XmlElementAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-113">Create an instance of the <xref:System.Xml.Serialization.XmlElementAttribute> class.</span></span>  
  
2.  <span data-ttu-id="d0aeb-114">Defina o <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> do <xref:System.Xml.Serialization.XmlElementAttribute> como "BookID".</span><span class="sxs-lookup"><span data-stu-id="d0aeb-114">Set the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> of the <xref:System.Xml.Serialization.XmlElementAttribute> to "BookID".</span></span>  
  
3.  <span data-ttu-id="d0aeb-115">Crie uma instância da classe <xref:System.Xml.Serialization.XmlAttributes>.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-115">Create an instance of the <xref:System.Xml.Serialization.XmlAttributes> class.</span></span>  
  
4.  <span data-ttu-id="d0aeb-116">Adicione o objeto `XmlElementAttribute` à coleção acessada por meio da propriedade <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> de <xref:System.Xml.Serialization.XmlAttributes>.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-116">Add the `XmlElementAttribute` object to the collection accessed through the <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> property of <xref:System.Xml.Serialization.XmlAttributes> .</span></span>  
  
5.  <span data-ttu-id="d0aeb-117">Crie uma instância da classe <xref:System.Xml.Serialization.XmlAttributeOverrides>.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-117">Create an instance of the <xref:System.Xml.Serialization.XmlAttributeOverrides> class.</span></span>  
  
6.  <span data-ttu-id="d0aeb-118">Adicione o `XmlAttributes` ao <xref:System.Xml.Serialization.XmlAttributeOverrides>, passando o tipo do objeto para sobrescrever e o nome do membro que está sendo sobrescrito.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-118">Add the `XmlAttributes` to the <xref:System.Xml.Serialization.XmlAttributeOverrides>, passing the type of the object to override and the name of the member being overridden.</span></span>  
  
7.  <span data-ttu-id="d0aeb-119">Crie uma instância da classe `XmlSerializer` com `XmlAttributeOverrides`.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-119">Create an instance of the `XmlSerializer` class with `XmlAttributeOverrides`.</span></span>  
  
8.  <span data-ttu-id="d0aeb-120">Crie uma instância da classe `Book` e serialize-a ou desserialize-a.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-120">Create an instance of the `Book` class, and serialize or deserialize it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0aeb-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0aeb-121">Example</span></span>  
  
```vb  
Public Class SerializeOverride()  
    ' Creates an XmlElementAttribute with the alternate name.  
    Dim myElementAttribute As XmlElementAttribute = _  
    New XmlElementAttribute()  
    myElementAttribute.ElementName = "BookID"  
    Dim myAttributes As XmlAttributes = New XmlAttributes()  
    myAttributes.XmlElements.Add(myElementAttribute)  
    Dim myOverrides As XmlAttributeOverrides = New XmlAttributeOverrides()  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes)  
    Dim mySerializer As XmlSerializer = _  
    New XmlSerializer(GetType(Book), myOverrides)  
    Dim b As Book = New Book()  
    b.ISBN = "123456789"  
    ' Creates a StreamWriter to write the XML stream to.  
    Dim writer As StreamWriter = New StreamWriter("Book.xml")  
    mySerializer.Serialize(writer, b);  
End Class  
```  
  
```csharp  
public class SerializeOverride()  
{  
    // Creates an XmlElementAttribute with the alternate name.  
    XmlElementAttribute myElementAttribute = new XmlElementAttribute();  
    myElementAttribute.ElementName = "BookID";  
    XmlAttributes myAttributes = new XmlAttributes();  
    myAttributes.XmlElements.Add(myElementAttribute);  
    XmlAttributeOverrides myOverrides = new XmlAttributeOverrides();  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes);  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(Book), myOverrides)  
    Book b = new Book();  
    b.ISBN = "123456789"  
    // Creates a StreamWriter to write the XML stream to.  
    StreamWriter writer = new StreamWriter("Book.xml");  
    mySerializer.Serialize(writer, b);  
}  
```  
  
 <span data-ttu-id="d0aeb-122">O fluxo XML pode ter a seguinte aparência.</span><span class="sxs-lookup"><span data-stu-id="d0aeb-122">The XML stream might resemble the following.</span></span>  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0aeb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0aeb-123">See also</span></span>

- <xref:System.Xml.Serialization.XmlElementAttribute>  
- <xref:System.Xml.Serialization.XmlAttributes>  
- <xref:System.Xml.Serialization.XmlAttributeOverrides>  
- [<span data-ttu-id="d0aeb-124">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="d0aeb-124">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [<span data-ttu-id="d0aeb-125">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="d0aeb-125">XmlSerializer</span></span>](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx)  
- [<span data-ttu-id="d0aeb-126">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="d0aeb-126">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [<span data-ttu-id="d0aeb-127">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="d0aeb-127">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
- [<span data-ttu-id="d0aeb-128">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="d0aeb-128">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
