---
title: Lendo e gravando esquemas XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 241ff40448c3dca2846f9e420dc7df41427dc79d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46698982"
---
# <a name="reading-and-writing-xml-schemas"></a>Lendo e gravando esquemas XML
A API do SOM (Schema Object Model) pode ser usada para ler e gravar esquemas XSD de arquivos ou de outras origens e criar esquemas XML na memória usando as classes no namespace <xref:System.Xml.Schema?displayProperty=nameWithType> que mapeiam para as estruturas definidas na Recomendação de esquema XML do W3C (World Wide Web Consortium).  
  
## <a name="reading-and-writing-xml-schemas"></a>Lendo e gravando esquemas XML  
 A classe <xref:System.Xml.Schema.XmlSchema> fornece os métodos <xref:System.Xml.Schema.XmlSchema.Read%2A> e <xref:System.Xml.Schema.XmlSchema.Write%2A> para ler e gravar esquemas XML. O método <xref:System.Xml.Schema.XmlSchema.Read%2A> retorna um objeto <xref:System.Xml.Schema.XmlSchema> que representa o esquema XML e utiliza um <xref:System.Xml.Schema.ValidationEventHandler> opcional como um parâmetro para tratar avisos e erros de validação de esquema encontrados ao ler um esquema XML.  
  
 O método <xref:System.Xml.Schema.XmlSchema.Write%2A> grava esquemas XML nos objetos <xref:System.IO.Stream>, <xref:System.IO.TextWriter> e <xref:System.Xml.XmlWriter> e pode utilizar um objeto opcional <xref:System.Xml.XmlNamespaceManager> como um parâmetro. Um <xref:System.Xml.XmlNamespaceManager> é usado para tratar namespaces encontrados em um esquema XML. Para saber mais sobre a classe <xref:System.Xml.XmlNamespaceManager>, confira [Gerenciando namespaces em um documento XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 O exemplo de código a seguir ilustra esquemas XML de leitura e gravação de um arquivo e para um arquivo. O exemplo de código utiliza o arquivo `example.xsd`, lê-o em um objeto <xref:System.Xml.Schema.XmlSchema> usando o método `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> e, em seguida, grava o arquivo no console e em um novo arquivo `new.xsd`. O exemplo de código também fornece <xref:System.Xml.Schema.ValidationEventHandler> como um parâmetro para o método `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> para tratar todos os avisos ou erros de validação de esquema encontrados ao ler o esquema XML. Se o <xref:System.Xml.Schema.ValidationEventHandler> não for especificado (`null`), nenhum aviso ou erro será relatado.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 O exemplo utiliza o arquivo `example.xsd` como entrada.  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de modelo de objeto de esquema XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [Compilando esquemas XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
- [Percorrer esquemas XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [Edição de esquemas XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [Incluindo ou importando esquemas XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
- [XmlSchemaSet para compilação de esquema](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [Infoset de compilação pós-esquema](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
- [Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md) (Gerenciando namespaces em um documento XML)
