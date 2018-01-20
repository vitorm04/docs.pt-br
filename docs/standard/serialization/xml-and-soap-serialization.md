---
title: "Serialização XML e SOAP"
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
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1ac5e83d6daf9654c541dcd8a748717be3ed05d0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="xml-and-soap-serialization"></a>Serialização XML e SOAP
A serialização XML converte (serializa) as propriedades e os campos públicos de um objeto (ou os parâmetros e valores de retorno de métodos) em um fluxo XML que esteja de acordo com um documento XSD (linguagem de definição de esquema XML) específico. A serialização XML resulta em classes fortemente tipadas com propriedades e campos públicos que são convertidos em um formato serial (neste caso, em XML) para armazenamento ou transporte.  
  
 Como XML é um padrão aberto, o fluxo XML pode ser processado por qualquer aplicativo, quando necessário, independentemente da plataforma. Por exemplo, serviços Web XML criados com ASP.NET usam a classe <xref:System.Xml.Serialization.XmlSerializer> para criar fluxos XML que passam dados entre aplicativos de serviço Web XML por toda a Internet ou entre intranets. Por outro lado, a desserialização obtém esse fluxo XML e reconstrói o objeto.  
  
 A serialização XML também pode ser usada para serializar objetos em fluxos XML que atendam à especificação SOAP. SOAP é um protocolo baseado em XML, projetado especificamente para transportar chamadas de procedimentos usando XML.  
  
 Para serializar e desserializar objetos, use a classe <xref:System.Xml.Serialization.XmlSerializer>. Para criar as classes a serem serializadas, use a ferramenta de definição de esquema XML.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 Fornece uma definição geral de serialização, particularmente da serialização XML.  
  
 [Como serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 Fornece instruções passo a passo para serializar um objeto.  
  
 [Como desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 Fornece instruções passo a passo para desserializar um objeto.  
  
 [Exemplos de serialização XML](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 Fornece exemplos que demonstram os conceitos básicos da serialização XML.  
  
 [A ferramenta de definição de esquema XML e a serialização XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 Descreve como usar a ferramenta de definição de esquema XML para criar classes que aderem a um esquema XSD específico ou para gerar um esquema XML de um arquivo .dll.  
  
 [Controlando a serialização XML usando atributos](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 Descreve como controlar a serialização usando atributos.  
  
 [Atributos que controlam a serialização XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 Lista os atributos que são usados para controlar a serialização XML.  
  
 [Como especificar um nome de elemento alternativo para um fluxo XML](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 Apresenta um cenário avançado de como gerar vários fluxos XML substituindo a serialização.  
  
 [Como controlar a serialização de classes derivadas](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 Fornece um exemplo de como controlar a serialização de classes derivadas.  
  
 [Como qualificar elementos XML e nomes de atributos XML](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 Descreve como definir e controlar a maneira como namespaces XML são usados no fluxo XML.  
  
 [Serialização XML com Serviços Web XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 Explica como a serialização XML é usada em serviços Web XML.  
  
 [Como serializar um objeto como um fluxo XML codificado para SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 Descreve como usar a classe <xref:System.Xml.Serialization.XmlSerializer> para criar fluxos XML SOAP codificados em conformidade com a seção 5 do documento "Simple Object Access Protocol (SOAP) 1.1" do World Wide Web Consortium (www.w3.org).  
  
 [Como substituir a serialização XML de SOAP codificada](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 Descreve o processo para substituir a serialização XML de objetos, como mensagens SOAP.  
  
 [Atributos que controlam a serialização SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 Lista os atributos que são usados para controlar a serialização codificada por SOAP.  
  
 [\<Elemento system.xml.serialization>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 O elemento de configuração de nível superior para controlar a serialização XML.  
  
 Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 Controla o modo de serialização de objetos <xref:System.DateTime>.  
  
 Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 Contém tipos que são usados pela classe <xref:System.Xml.Serialization.XmlSchemaImporter>.  
  
 [Elemento \<add> para \<xmlSchemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 Adiciona tipos que são usados pela classe <xref:System.Xml.Serialization.XmlSchemaImporter>.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tecnologias de desenvolvimento avançadas](http://msdn.microsoft.com/library/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 Fornece links para obter mais informações sobre tarefas e técnicas sofisticadas de desenvolvimento no .NET Framework.  
  
 [Serviços Web XML criados com o ASP.NET e clientes de serviços Web XML](http://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)  
 Fornece tópicos que descrevem e explicam como programar serviços Web XML usando ASP.NET.  
  
## <a name="see-also"></a>Consulte também  
 [Serialização binária](../../../docs/standard/serialization/binary-serialization.md)
