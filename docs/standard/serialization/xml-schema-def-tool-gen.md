---
title: Como usar a ferramenta de definição de esquema XML para gerar classes e documentos de esquema XML
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 2edaf7ba540035fbf2f49ba78b41ab99f8889391
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583042"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>Como usar a ferramenta de definição de esquema XML para gerar classes e documentos de esquema XML
A ferramenta de Definição de Esquema XML (Xsd.exe) permite gerar um esquema XML que descreve uma classe ou gerar a classe definida por um esquema XML. Os seguintes procedimentos mostram como executar essas operações.  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>Para gerar classes que estão em conformidade com um esquema específico  
  
1.  Abra um prompt de comando.  
  
2.  Passe o esquema XML como um argumento para a ferramenta de definição de esquema XML, que cria um conjunto de classes que correspondem precisamente ao Esquema XML, por exemplo:  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     A ferramenta somente pode processar esquemas que fazem referência à especificação de XML World Wide Web Consortium de 16 de março de 2001. Em outras palavras, o namespace do esquema XML deve ser "http://www.w3.org/2001/XMLSchema" conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  Modifique as classes com métodos, propriedades ou campos, conforme o necessário. Para obter mais informações sobre como modificar uma classe com atributos, consulte [Controlando a serialização XML usando atributos](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) e [Atributos que controlam a serialização SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 É geralmente útil examinar o esquema do fluxo de XML que é gerado quando instâncias de uma classe (ou classes) são serializadas. Por exemplo, você pode publicar seu esquema para outros usarem ou pode compará-lo com um esquema com o qual está tentando obter conformidade.  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>Para gerar um documento de esquema XML de um conjunto de classes  
  
1.  Compile uma classe ou classes em uma DLL.  
  
2.  Abra um prompt de comando.  
  
3.  Passe a DLL como argumento para Xsd.exe, por exemplo:  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     O esquema (ou esquemas) serão escritos, começando com o nome "schema0.xsd".  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataSet>  
- [A ferramenta de definição de esquema XML e a serialização XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
- [Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [Ferramenta de Definição de Esquema XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
- <xref:System.Xml.Serialization.XmlSerializer>  
- [Como serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [Como desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
