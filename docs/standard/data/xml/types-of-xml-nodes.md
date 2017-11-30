---
title: "Tipos de nós XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3914a2c5c06a2cc73f14bc473984094b474d537e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-xml-nodes"></a>Tipos de nós XML
Quando um documento XML é lido na memória como uma árvore de nós, os tipos de nós são decididos quando os nós são criados. A especificação DOM (Document Object Model) XML tem vários tipos de nós, determinados pelo W3C (World Wide Web Consortium) e listados na seção 1.1.1 (The DOM Structure Model). A tabela a seguir lista os tipos de nós, o objeto atribuído ao tipo de nó e uma breve descrição de cada tipo.  
  
|Tipo de nó DOM|Objeto|Descrição|  
|-------------------|------------|-----------------|  
|Documento|<xref:System.Xml.XmlDocument>|O contêiner de todos os nós na árvore. Também é conhecido como diretório base, que nem sempre é o mesmo do elemento raiz.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Um recipiente temporário que contém um ou mais nós sem nenhuma estrutura de árvore.|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|Representa o nó `<!DOCTYPE…>`.|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|Representa o texto de referência de entidade não expandido.|  
|Elemento|<xref:System.Xml.XmlElement>|Representa um nó de elemento.|  
|Attr|<xref:System.Xml.XmlAttribute>|Atributo de um elemento.|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|Nó de instrução de processamento.|  
|Comentário|<xref:System.Xml.XmlComment>|Um nó de comentário.|  
|Texto|<xref:System.Xml.XmlText>|Texto que pertence a um elemento ou a um atributo.|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|Representa CDATA.|  
|Entidade|<xref:System.Xml.XmlEntity>|Representa as declarações `<!ENTITY…>` em um documento XML, de um subconjunto de DTDs (definição de tipo de documento) internas ou de DTDs externas e de entidades de parâmetro.|  
|Notation|<xref:System.Xml.XmlNotation>|Representa uma notação declarada na DTD.|  
  
 Mesmo que um atributo (*attr*) é listado no nível 1 do DOM do W3C seção 1.2 fundamentais Interfaces como um nó, ele não é considerado um filho de qualquer nó do elemento.  
  
 A tabela a seguir mostra os tipos de nó adicional não definidos pelo W3C, mas eles estão disponíveis para uso no modelo de objeto do Microsoft .NET Framework como **XmlNodeType** enumerações. Portanto, não há nenhuma coluna de tipo de nó DOM correspondente com esses tipos de nós.  
  
|Tipo de nó|Descrição|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Representa o nó de declaração `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Representa o espaço em branco significativo, que é o espaço em branco com conteúdo misto.|  
|<xref:System.Xml.XmlWhitespace>|Representa o espaço em branco no conteúdo de um elemento.|  
|EndElement|Retornado quando **XmlReader** obtém ao final de um elemento.<br /><br /> Exemplo de XML:  **\< /item >**<br /><br /> Para obter mais informações, consulte <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Retornado quando **XmlReader** chegar ao fim da substituição de entidade como resultado de uma chamada para <xref:System.Xml.XmlReader.ResolveEntity%2A>. Para obter mais informações, consulte <xref:System.Xml.XmlNodeType>.|  
  
 Para ver um exemplo de código que lê em XML e usa uma construção caso os tipos de nó para imprimir informações sobre o nó e seu conteúdo, consulte <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.  
  
 Para obter mais informações sobre a hierarquia de objetos dos tipos de nó e o nome do objeto equivalente, consulte [hierarquia de modelo de objeto de documento (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md). Para obter mais informações sobre os objetos criados na árvore de nós, consulte [mapeando a hierarquia de objetos para dados XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
