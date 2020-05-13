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
ms.openlocfilehash: 09f1431d05248ef3ac3fdcf24bca35ff5cc2e22b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378392"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="456c5-104">Como serializar um objeto como um fluxo XML codificado para SOAP</span><span class="sxs-lookup"><span data-stu-id="456c5-104">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="456c5-105">Como a mensagem de SOAP é criada usando XML, a classe <xref:System.Xml.Serialization.XmlSerializer> pode ser usado para serializar classes e gerar mensagens SOAP codificadas.</span><span class="sxs-lookup"><span data-stu-id="456c5-105">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="456c5-106">O XML resultante está em conformidade com a [seção 5 do documento "Protocolo SOAP 1.1" do World Wide Web Consortium](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="456c5-106">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="456c5-107">Quando você está criando um serviço Web XML que se comunica por meio de mensagens SOAP, pode personalizar o fluxo XML aplicando um conjunto de atributos SOAP especiais para classes e membros de classes.</span><span class="sxs-lookup"><span data-stu-id="456c5-107">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="456c5-108">Para obter mais informações, consulte [Atributos que controlam a serialização SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="456c5-108">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="456c5-109">Para serializar um objeto como um fluxo XML codificado para SOAP</span><span class="sxs-lookup"><span data-stu-id="456c5-109">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="456c5-110">Criar a classe usando a [Ferramenta de Definição de Esquema XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="456c5-110">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="456c5-111">Aplique um ou mais dos atributos especiais localizados em `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="456c5-111">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="456c5-112">Consulte a lista em "Atributos que controlam a serialização SOAP codificada".</span><span class="sxs-lookup"><span data-stu-id="456c5-112">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="456c5-113">Crie um `XmlTypeMapping` criando um novo `SoapReflectionImporter` e invocando o método `ImportTypeMapping` com o tipo da classe serializada.</span><span class="sxs-lookup"><span data-stu-id="456c5-113">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="456c5-114">O exemplo de código a seguir chama o método `ImportTypeMapping` da classe `SoapReflectionImporter` para criar um `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="456c5-114">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4. <span data-ttu-id="456c5-115">Cria uma instância da classe `XmlSerializer` passando o `XmlTypeMapping` para o construtor <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29>.</span><span class="sxs-lookup"><span data-stu-id="456c5-115">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="456c5-116">Chame o método `Serialize` or `Deserialize`.</span><span class="sxs-lookup"><span data-stu-id="456c5-116">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="456c5-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="456c5-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="456c5-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="456c5-118">See also</span></span>

- [<span data-ttu-id="456c5-119">Serialização de XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="456c5-119">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [<span data-ttu-id="456c5-120">Atributos que controlam a serialização SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="456c5-120">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="456c5-121">Serialização XML com serviços Web XML</span><span class="sxs-lookup"><span data-stu-id="456c5-121">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="456c5-122">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="456c5-122">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="456c5-123">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="456c5-123">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="456c5-124">Como substituir a serialização XML de SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="456c5-124">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
