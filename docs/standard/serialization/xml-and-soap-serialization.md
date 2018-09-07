---
title: Serialização XML e SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: 366a4a42ff0bf968e51e11a66fa81566a47c86ea
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075277"
---
# <a name="xml-and-soap-serialization"></a>Serialização XML e SOAP

A serialização XML converte (serializa) as propriedades e os campos públicos de um objeto (ou os parâmetros e valores de retorno de métodos) em um fluxo XML que esteja de acordo com um documento XSD (linguagem de definição de esquema XML) específico. A serialização XML resulta em classes fortemente tipadas com propriedades e campos públicos que são convertidos em um formato serial (neste caso, em XML) para armazenamento ou transporte.

Como XML é um padrão aberto, o fluxo XML pode ser processado por qualquer aplicativo, quando necessário, independentemente da plataforma. Por exemplo, serviços Web XML criados com ASP.NET usam a classe <xref:System.Xml.Serialization.XmlSerializer> para criar fluxos XML que passam dados entre aplicativos de serviço Web XML por toda a Internet ou entre intranets. Por outro lado, a desserialização obtém esse fluxo XML e reconstrói o objeto.

A serialização XML também pode ser usada para serializar objetos em fluxos XML que atendam à especificação SOAP. SOAP é um protocolo baseado em XML, projetado especificamente para transportar chamadas de procedimentos usando XML.

Para serializar e desserializar objetos, use a classe <xref:System.Xml.Serialization.XmlSerializer>. Para criar as classes a serem serializadas, use a ferramenta de definição de esquema XML.

## <a name="in-this-section"></a>Nesta seção

[Apresentando a serialização XML](introducing-xml-serialization.md)  
Fornece uma definição geral de serialização, particularmente da serialização XML.

[Como serializar um objeto](how-to-serialize-an-object.md)  
Fornece instruções passo a passo para serializar um objeto.

[Como desserializar um objeto](how-to-deserialize-an-object.md)  
Fornece instruções passo a passo para desserializar um objeto.

[Exemplos de serialização XML](examples-of-xml-serialization.md)  
Fornece exemplos que demonstram os conceitos básicos da serialização XML.

[A ferramenta de definição de esquema XML e a serialização XML](the-xml-schema-definition-tool-and-xml-serialization.md)  
Descreve como usar a ferramenta de definição de esquema XML para criar classes que aderem a um esquema XSD específico ou para gerar um esquema XML de um arquivo .dll.

[Controlando a serialização XML usando atributos](controlling-xml-serialization-using-attributes.md)  
Descreve como controlar a serialização usando atributos.

[Atributos que controlam a serialização XML](attributes-that-control-xml-serialization.md)  
Lista os atributos que são usados para controlar a serialização XML.

[Como especificar um nome de elemento alternativo para um fluxo XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
Apresenta um cenário avançado de como gerar vários fluxos XML substituindo a serialização.

[Como controlar a serialização de classes derivadas](how-to-control-serialization-of-derived-classes.md)  
Fornece um exemplo de como controlar a serialização de classes derivadas.

[Como qualificar elementos XML e nomes de atributos XML](how-to-qualify-xml-element-and-xml-attribute-names.md)  
Descreve como definir e controlar a maneira como namespaces XML são usados no fluxo XML.

[Serialização XML com Serviços Web XML](xml-serialization-with-xml-web-services.md)  
Explica como a serialização XML é usada em serviços Web XML.

[Como serializar um objeto como um fluxo XML codificado para SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
Descreve como usar o <xref:System.Xml.Serialization.XmlSerializer> classe para criar fluxos XML SOAP codificados que estão em conformidade com a seção 5 do documento do World Wide Web Consortium (W3C) [simples objeto Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).

[Como substituir a serialização XML de SOAP codificada](how-to-override-encoded-soap-xml-serialization.md)  
Descreve o processo para substituir a serialização XML de objetos, como mensagens SOAP.

[Atributos que controlam a serialização SOAP codificada](attributes-that-control-encoded-soap-serialization.md)  
Lista os atributos que são usados para controlar a serialização codificada por SOAP.

[\<Elemento system.xml.serialization>](system-xml-serialization-element.md)  
O elemento de configuração de nível superior para controlar a serialização XML.

Elemento [\<dateTimeSerialization>](datetimeserialization-element.md)  
Controla o modo de serialização de objetos <xref:System.DateTime>.

Elemento [\<schemaImporterExtensions>](schemaimporterextensions-element.md)  
Contém tipos que são usados pela classe <xref:System.Xml.Serialization.XmlSchemaImporter>.

[\<Adicionar > elemento para \<schemaImporterExtensions >](add-element-for-schemaimporterextensions.md)  
Adiciona tipos que são usados pela classe <xref:System.Xml.Serialization.XmlSchemaImporter>.

## <a name="related-sections"></a>Seções relacionadas

[Tecnologias de desenvolvimento avançadas](https://msdn.microsoft.com/library/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
Fornece links para obter mais informações sobre tarefas e técnicas sofisticadas de desenvolvimento no .NET Framework.

[Serviços Web XML criados com o ASP.NET e clientes de serviços Web XML](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)  
Fornece tópicos que descrevem e explicam como programar serviços Web XML usando ASP.NET.

## <a name="see-also"></a>Consulte também

- [Serialização binária](binary-serialization.md)
