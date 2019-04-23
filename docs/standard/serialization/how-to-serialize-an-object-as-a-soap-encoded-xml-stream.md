---
title: 'Como: serializar um objeto como um fluxo XML codificado para SOAP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: bfbdda0861a6f2867a2e7003dd7054129fd343b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334517"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Como: serializar um objeto como um fluxo XML codificado para SOAP
  
 Como a mensagem de SOAP é criada usando XML, a classe <xref:System.Xml.Serialization.XmlSerializer> pode ser usado para serializar classes e gerar mensagens SOAP codificadas. O XML resultante está em conformidade com a [seção 5 do documento "Protocolo SOAP 1.1" do World Wide Web Consortium](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512). Quando você está criando um serviço Web XML que se comunica por meio de mensagens SOAP, pode personalizar o fluxo XML aplicando um conjunto de atributos SOAP especiais para classes e membros de classes. Para obter mais informações, consulte [Atributos que controlam a serialização SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Para serializar um objeto como um fluxo XML codificado para SOAP  
  
1. Criar a classe usando a [Ferramenta de Definição de Esquema XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
2. Aplique um ou mais dos atributos especiais localizados em `System.Xml.Serialization`. Consulte a lista em "Atributos que controlam a serialização SOAP codificada".  
  
3. Crie um `XmlTypeMapping` criando um novo `SoapReflectionImporter` e invocando o método `ImportTypeMapping` com o tipo da classe serializada.  
  
     O exemplo de código a seguir chama o método `ImportTypeMapping` da classe `SoapReflectionImporter` para criar um `XmlTypeMapping`.  
  
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
  
4. Cria uma instância da classe `XmlSerializer` passando o `XmlTypeMapping` para o construtor <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29>.  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. Chame o método `Serialize` or `Deserialize`.  
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="see-also"></a>Consulte também

- [Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [Atributos que controlam a serialização SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [Serialização XML com Serviços Web XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [Como: Serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Como: Desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [Como: Substituir a serialização de XML de SOAP codificada](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
