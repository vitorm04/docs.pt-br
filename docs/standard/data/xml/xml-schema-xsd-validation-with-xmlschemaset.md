---
title: "Validação de XSD (esquema XML) com XmlSchemaSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a6cf857ccecbdac88453fd1fba6e93d609196b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Validação de XSD (esquema XML) com XmlSchemaSet
Documentos XML podem ser validados em um esquema da linguagem XSD em um <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Validando documentos XML  
 Documentos XML são validados pelo método <xref:System.Xml.XmlReader.Create%2A> da classe <xref:System.Xml.XmlReader>. Para validar um documento XML, construa um objeto <xref:System.Xml.XmlReaderSettings> que contém uma linguagem XSD com a qual validar o documento XML.  
  
> [!NOTE]
>  O <xref:System.Xml.Schema> namespace contém métodos de extensão que tornam mais fácil validar uma árvore XML em um arquivo XSD ao usar [LINQ para XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). Para obter mais informações sobre como validar documentos XML com LINQ to XML, consulte [como: validar usando XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).  
  
 Um esquema individual ou um conjunto de esquemas (como <xref:System.Xml.Schema.XmlSchemaSet>) podem ser adicionados a um <xref:System.Xml.Schema.XmlSchemaSet> passando qualquer um como um parâmetro para o método <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet>. Observe que, ao validar um documento, o namespace de destino do documento deve corresponder ao namespace de destino do esquema no conjunto de esquema.  
  
 Veja a seguir um documento XML de exemplo.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Veja a seguir o esquema que valida o documento XML de exemplo.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 No exemplo de código a seguir, o esquema acima é adicionado à propriedade <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> do objeto <xref:System.Xml.XmlReaderSettings>. O objeto <xref:System.Xml.XmlReaderSettings> é passado como um parâmetro para o método <xref:System.Xml.XmlReader.Create%2A> do objeto <xref:System.Xml.XmlReader>, que valida o documento XML acima.  
  
 A propriedade <xref:System.Xml.XmlReaderSettings.ValidationType%2A> do objeto <xref:System.Xml.XmlReaderSettings> é definida como `Schema` para aplicar a validação o documento XML pelo método <xref:System.Xml.XmlReader.Create%2A> do objeto <xref:System.Xml.XmlReader>. Um <xref:System.Xml.Schema.ValidationEventHandler> é adicionado ao objeto <xref:System.Xml.XmlReaderSettings> para manipular qualquer evento <xref:System.Xml.Schema.XmlSeverityType.Warning> ou <xref:System.Xml.Schema.XmlSeverityType.Error> gerado por erros encontrados durante o processo de validação do documento XML e do esquema.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [XmlSchemaSet para compilação de esquema](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Trabalhando com esquemas XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
