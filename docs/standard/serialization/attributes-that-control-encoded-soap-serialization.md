---
title: "Atributos que controlam a serialização SOAP codificada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 358b635ee74699d9d427e8fac23fabd70c6cfa98
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Atributos que controlam a serialização SOAP codificada 
O documento do World Wide Web Consortium (www.w3.org) intitulado “Simple Object Access Protocol (SOAP) 1.1” (Protocolo SOAP 1.1) contém uma seção opcional (seção 5) que descreve como os parâmetros SOAP podem ser codificados. Para estar em conformidade com a seção 5 da especificação, é necessário usar um conjunto especial de atributos encontrados no namespace <xref:System.Xml.Serialization>. Aplique esses atributos conforme for apropriado a classes e membros das classes e, em seguida, use o <xref:System.Xml.Serialization.XmlSerializer> para serializar instâncias da classe ou classes.  
  
 A tabela a seguir mostra os atributos, onde podem ser aplicados e o que eles fazem. Para obter mais informações sobre como usar esses atributos para controlar a serialização XML, consulte [Como serializar um objeto como um fluxo XML codificado em SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) e [Como substituir a serialização XML de SOAP codificada](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).  
  
 Para obter mais informações sobre atributos, consulte [Atributos](../../../docs/standard/attributes/index.md).  
  
|Atributo|Aplica-se a|Especifica|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|Campo público, propriedade, parâmetro ou valor de retorno.|O membro da classe será serializado como um atributo XML.|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|Campo público, propriedade, parâmetro ou valor de retorno.|A classe será serializada como um elemento XML.|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|O campo público que é um identificador de enumeração.|O nome do elemento de um membro de enumeração.|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|Propriedades públicas e campos.|A propriedade ou campo devem ser ignorados quando a classe recipiente é serializada.|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|Declarações públicas de classe derivada e métodos públicos para documentos da linguagem WSDL.|O tipo deve ser incluído ao gerar esquemas (para serem reconhecidos quando serializados).|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|Declarações públicas de classe.|A classe deverá ser serializada como um tipo XML.|  
  
## <a name="see-also"></a>Consulte também  
 [Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Como serializar um objeto como um fluxo XML codificado para SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [Como substituir a serialização XML de SOAP codificada](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [Atributos](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Como serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Como desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
