---
title: Atributos que controlam a serialização SOAP codificada
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 07c4c1e9b9a9da2e9a585efdcac644c616012078
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934388"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Atributos que controlam a serialização SOAP codificada

O documento do World Wide Web Consortium (W3C) chamado [simples objeto Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contém uma seção opcional (seção 5) que descreve como os parâmetros SOAP podem ser codificados. Para estar em conformidade com a seção 5 da especificação, é necessário usar um conjunto especial de atributos encontrados no namespace <xref:System.Xml.Serialization>. Aplique esses atributos conforme for apropriado a classes e membros das classes e, em seguida, use o <xref:System.Xml.Serialization.XmlSerializer> para serializar instâncias da classe ou classes.

A tabela a seguir mostra os atributos, onde podem ser aplicados e o que eles fazem. Para obter mais informações sobre como usar esses atributos para controlar a serialização XML, consulte [Como serializar um objeto como um fluxo XML codificado em SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) e [Como substituir a serialização XML de SOAP codificada](how-to-override-encoded-soap-xml-serialization.md).

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

[Serialização XML e SOAP](xml-and-soap-serialization.md)  
[Como serializar um objeto como um fluxo XML codificado para SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
[Como substituir a serialização XML de SOAP codificada](how-to-override-encoded-soap-xml-serialization.md)  
[Atributos](../../../docs/standard/attributes/index.md)  
<xref:System.Xml.Serialization.XmlSerializer>  
[Como serializar um objeto](how-to-serialize-an-object.md)  
[Como desserializar um objeto](how-to-deserialize-an-object.md)