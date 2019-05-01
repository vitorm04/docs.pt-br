---
title: A ferramenta de definição de esquema XML e a serialização XML
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: 4c950d84cc95c20c2ae85340a2987ea51bed9570
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028285"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a>A ferramenta de definição de esquema XML e a serialização XML
A ferramenta de Definição de Esquema XML ([Ferramenta de Definição de Esquema XML [Xsd.exe]](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) é instalada junto com as ferramentas do .NET Framework como parte do Software Development Kit do Windows® (SDK do Windows). A ferramenta é criada principalmente para duas finalidades:  
  
- Para gerar arquivos de classe C# ou Visual Basic que estejam em conformidade com um esquema específico de linguagem XSD. A ferramenta usa um esquema XML como um argumento e gera um arquivo que contém um número de classes que, quando serializadas com o <xref:System.Xml.Serialization.XmlSerializer>, estão em conformidade com o esquema. Para obter informações sobre como usar a ferramenta para gerar classes que estão em conformidade com um esquema específico, consulte [como: Use a ferramenta de definição de esquema XML para gerar Classes e documentos de esquema XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).  
  
- Para gerar um documento de esquema XML de um arquivo .dll ou .exe. Para ver o esquema de um conjunto de arquivos que você criou ou um que tenha sido alterado com atributos, passe o DLL ou EXE como um argumento para a ferramenta para gerar o esquema XML. Para obter informações sobre como usar a ferramenta para gerar um documento de esquema XML de um conjunto de classes, consulte [como: Use a ferramenta de definição de esquema XML para gerar Classes e documentos de esquema XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).  
  
 Para obter mais informações sobre essa ferramenta e outras, consulte [Ferramentas](../../../docs/framework/tools/index.md). Para obter informações sobre as opções da ferramenta, consulte [Ferramenta de Definição de Esquema XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataSet>
- [Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Ferramenta de Definição de Esquema XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Como: Serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Como: Desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [Como: Use a ferramenta de definição de esquema XML para gerar Classes e documentos de esquema XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- [Suporte à associação de esquema XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))
