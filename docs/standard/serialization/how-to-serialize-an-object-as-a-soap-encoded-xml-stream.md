---
title: Como serializar um objeto como um fluxo XML codificado para SOAP
description: Saiba como serializar um objeto como um fluxo XML codificado em SOAP. A classe XmlSerializer pode ser usada para serializar classes e gerar mensagens SOAP codificadas.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: 1d38c4e334439ef41b4d4429e52cff04c6463573
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291559"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="ae26e-104">Como serializar um objeto como um fluxo XML codificado para SOAP</span><span class="sxs-lookup"><span data-stu-id="ae26e-104">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="ae26e-105">Como a mensagem de SOAP é criada usando XML, a classe <xref:System.Xml.Serialization.XmlSerializer> pode ser usado para serializar classes e gerar mensagens SOAP codificadas.</span><span class="sxs-lookup"><span data-stu-id="ae26e-105">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="ae26e-106">O XML resultante está em conformidade com a [seção 5 do documento "Protocolo SOAP 1.1" do World Wide Web Consortium](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="ae26e-106">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="ae26e-107">Quando você está criando um serviço Web XML que se comunica por meio de mensagens SOAP, pode personalizar o fluxo XML aplicando um conjunto de atributos SOAP especiais para classes e membros de classes.</span><span class="sxs-lookup"><span data-stu-id="ae26e-107">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="ae26e-108">Para obter mais informações, consulte [Atributos que controlam a serialização SOAP codificada](attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ae26e-108">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="ae26e-109">Para serializar um objeto como um fluxo XML codificado para SOAP</span><span class="sxs-lookup"><span data-stu-id="ae26e-109">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="ae26e-110">Criar a classe usando a [Ferramenta de Definição de Esquema XML (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ae26e-110">Create the class using the [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="ae26e-111">Aplique um ou mais dos atributos especiais localizados em `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="ae26e-111">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="ae26e-112">Consulte a lista em "Atributos que controlam a serialização SOAP codificada".</span><span class="sxs-lookup"><span data-stu-id="ae26e-112">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="ae26e-113">Crie um `XmlTypeMapping` criando um novo `SoapReflectionImporter` e invocando o método `ImportTypeMapping` com o tipo da classe serializada.</span><span class="sxs-lookup"><span data-stu-id="ae26e-113">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="ae26e-114">O exemplo de código a seguir chama o método `ImportTypeMapping` da classe `SoapReflectionImporter` para criar um `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="ae26e-114">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4. <span data-ttu-id="ae26e-115">Cria uma instância da classe `XmlSerializer` passando o `XmlTypeMapping` para o construtor <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29>.</span><span class="sxs-lookup"><span data-stu-id="ae26e-115">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="ae26e-116">Chame o método `Serialize` or `Deserialize`.</span><span class="sxs-lookup"><span data-stu-id="ae26e-116">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae26e-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae26e-117">Example</span></span>  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae26e-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="ae26e-118">See also</span></span>

- [<span data-ttu-id="ae26e-119">Serialização de XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="ae26e-119">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="ae26e-120">Atributos que controlam a serialização SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="ae26e-120">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="ae26e-121">Serialização XML com serviços Web XML</span><span class="sxs-lookup"><span data-stu-id="ae26e-121">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="ae26e-122">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="ae26e-122">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="ae26e-123">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="ae26e-123">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="ae26e-124">Como substituir a serialização XML de SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="ae26e-124">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
