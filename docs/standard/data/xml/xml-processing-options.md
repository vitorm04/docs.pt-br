---
title: "Opções de processamento XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 18f8f9c76a1842517340eaa3f74b4778f869403e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-options"></a>Opções de processamento XML
Consulte as tabelas a seguir para obter uma lista das tecnologias da Microsoft que você pode usar para processar dados XML.  
  
## <a name="net-framework-options"></a>Opções do .NET Framework  
  
|**Opção**|**Tipo de processamento**|**Descrição**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(namespace <xref:System.Xml.Linq>)|Na memória|-Com base na tecnologia .NET Framework Language-Integrated LINQ (consulta).<br />-Fornece a experiência de consulta que é semelhante ao SQL para objetos, dados relacionais e dados XML.<br />-Fornece inituive recursos de criação e transformação de documento.<br />-Use esta opção se você estiver escrevendo o novo código.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Com base em fluxo|-Fornece uma maneira rápida, não armazenado em cache, somente de encaminhamento para acessar dados XML.<br />-Você pode criar objetos usando o <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> método e especifique o conjunto de recursos para habilitar o objeto usando o <xref:System.Xml.XmlReaderSettings> classe.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Com base em fluxo|-Fornece uma maneira rápida não armazenado em cache, somente de encaminhamento de gerar dados XML.<br />-Você pode criar objetos usando o <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> método e especifique o conjunto de recursos para habilitar o objeto usando o <xref:System.Xml.XmlWriterSettings> classe.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|Na memória|-Implementa o [principal de nível 1 do modelo de objeto de documento (DOM) W3C](http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) e [DOM nível 2 Core](http://www.w3.org/TR/DOM-Level-2-Core/) recomendações.<br />-Você pode criar, inserir, remover e modificar nós usando métodos e propriedades com base no modelo familiar de DOM.<br />-Use esta opção se você estiver modificando um código existente que utiliza o DOM do W3C.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|Na memória|-Oferece várias opções de edição e recursos de navegação usando um modelo de cursor.<br />-Documentos XML podem estar contidos em um <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> objeto.<br />-Oferece excelente desempenho para processamento de somente leitura do XML.<br />-Use esta opção se você estiver modificando o código existente com consultas XPath ou transformações XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|Na memória|-Fornece opções para transformar dados XML usando transformações XSL.<br />-A [compilador de XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) permite que você faz referência pré-compilado transformações em seu aplicativo.|  
  
## <a name="win32-and-com-based-options"></a>Opções Win32 e baseadas em COM  
  
|**Opção**|**Descrição**|  
|----------------|---------------------|  
|[XmlLite](http://go.microsoft.com/fwlink/?LinkId=93723)|-Um rápida e seguro, não em cache, somente de encaminhamento analisador XML que ajuda você a criar alto desempenho aplicativos XML.<br />-Funciona com qualquer linguagem que pode usar bibliotecas de vínculo dinâmico (DLLs); é recomendável usar o C++.|  
|[MSXML](http://go.microsoft.com/fwlink/?LinkId=93722)|-Baseado em COM tecnologia para processamento de XML que está incluído no sistema operacional Windows.<br />-Fornece uma implementação nativa do DOM com suporte para XPath e XSLT.<br />-Contém o SAX2 baseado em evento analisador.|  
  
## <a name="see-also"></a>Consulte também  
 [Processar dados XML usando o modelo DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [Processar dados XML usando o modelo de dados XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Compilador XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
