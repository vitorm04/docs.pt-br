---
title: Trabalhando com esquemas XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e21d402dce02ecb332d041f0cda651df911979ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-xml-schemas"></a>Trabalhando com esquemas XML
Para definir a estrutura de um documento XML, bem como os relacionamentos de seus elementos, tipos de dados e restrições de conteúdo, você usa uma DTD (definição de tipo de documento) ou um esquema XSD (linguagem de definição de esquema XML). Embora um documento XML seja considerado bem-formado se atender a todos os requisitos sintáticos definidos pela Recomendação da linguagem XML 1.0 do W3C (World Wide Web Consortium), ele não é considerado válido a menos que seja bem-formado e esteja de acordo com as restrições definidas pela DTD ou o esquema. Portanto, embora todos os documentos XML válidos sejam bem-formados, nem todos os documentos XML bem-formados são válidos.  
  
 Para obter mais informações sobre XML, consulte o [recomendação do W3C XML 1.0](http://go.microsoft.com/fwlink/?linkid=7269). Para obter mais informações sobre o esquema XML, consulte o [W3C XML Schema Part 1: estruturas recomendação](http://go.microsoft.com/fwlink/?linkid=48881) e [W3C XML Schema Part 2: recomendação de tipos de dados](http://go.microsoft.com/fwlink/?linkid=17392) recomendações.  
  
## <a name="in-this-section"></a>Nesta seção  
 [XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md) [SOM (Modelo de Objeto de Esquema) XML]  
 Discute o SOM (Schema Object Model) no namespace <xref:System.Xml.Schema?displayProperty=nameWithType> que fornece um conjunto de classes que permitem que você leia um esquema XSD (linguagem de definição de esquema XML) em um arquivo ou crie programaticamente um esquema na memória.  
  
 [XmlSchemaSet para compilação de esquema](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 Discute a classe <xref:System.Xml.Schema.XmlSchemaSet> que é um cache onde os esquemas XSD podem ser armazenados e validados.  
  
 [XmlSchemaValidator envio-de validação](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 Discute a classe <xref:System.Xml.Schema.XmlSchemaValidator>, que fornece um mecanismo eficiente e de alto desempenho para validar dados XML em esquemas XSD de uma maneira baseada em push.  
  
 [Inferindo um esquema XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 Discute como usar a classe <xref:System.Xml.Schema.XmlSchemaInference> para inferir um esquema XSD na estrutura de um documento XML.  
  
## <a name="reference"></a>Referência  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Validando um documento XML no DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 Discute como validar o XML no DOM (Document Object Model). Você pode validar o XML como é carregado no DOM ou validar um documento XML invalidado anteriormente no DOM.  
  
 [Validação de esquema usando XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Discute como validar XML que está sendo navegado e editado usando a classe <xref:System.Xml.XPath.XPathNavigator>.
