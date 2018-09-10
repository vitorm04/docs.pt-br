---
title: Opções de processamento XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e0d0a2a8d8c7fd75da7f2109619d588eac7b4a6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863014"
---
# <a name="xml-processing-options"></a>Opções de processamento XML
Veja nas tabelas a seguir uma lista das tecnologias da Microsoft que você pode usar para processar dados XML.  
  
## <a name="net-framework-options"></a>Opções do .NET Framework  
  
|**Opção**|**Tipo de processamento**|**Descrição**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(namespace <xref:System.Xml.Linq>)|Na memória|-   Com base na tecnologia LINQ (Consulta Integrada à Linguagem) do .NET Framework.<br />-   Fornece a experiência de consulta que é semelhante ao SQL para objetos, dados relacionais e dados XML.<br />-   Fornece recursos intuitivos de criação e transformação de documentos.<br />-   Use esta opção se estiver escrevendo um novo código.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Com base em fluxo|-   Fornece uma maneira rápida, não armazenado em cache, somente de encaminhamento, de acessar dados XML.<br />-   Você pode criar objetos usando o método <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> e especificar o conjunto de recursos para habilitar no objeto usando a classe <xref:System.Xml.XmlReaderSettings>.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Com base em fluxo|-   Fornece uma maneira rápida, não armazenado em cache, somente de encaminhamento, de gerar dados XML.<br />-   Você pode criar objetos usando o método <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> e especificar o conjunto de recursos para habilitar no objeto usando a classe <xref:System.Xml.XmlWriterSettings>.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|Na memória|-   Implementa as recomendações do [DOM (Modelo de Objeto do Documento) Core do W3C nível 1](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) e do [DOM Core nível 2](https://www.w3.org/TR/DOM-Level-2-Core/).<br />-   Os nós podem ser criados, inseridos, removidos e alterados usando os métodos e propriedades com base no modelo DOM familiar.<br />-   Use esta opção se você estiver modificando um código existente que utiliza o DOM do W3C.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|Na memória|-   Oferece várias opções de edição e recursos de navegação usando um modelo do cursor.<br />-   Os documentos XML podem estar contidos em um objeto <xref:System.Xml.XPath.XPathDocument> ou objeto <xref:System.Xml.XmlDocument>.<br />-   Oferece um desempenho excelente para o processamento somente leitura do XML.<br />-   Use esta opção se você estiver modificando o código existente com consultas XPath ou transformações XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|Na memória|-   Fornece opções para transformar os dados XML usando transformações XSL.<br />-   O [Compilador de XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) permite que você faça referência a transformações pré-compiladas em seu aplicativo.|  
  
## <a name="win32-and-com-based-options"></a>Opções Win32 e baseadas em COM  
  
|**Opção**|**Descrição**|  
|----------------|---------------------|  
|[XmlLite](https://msdn.microsoft.com/library/ms752872.aspx)|-   Um analisador XML rápido, seguro, não armazenado em cache, apenas de encaminhamento que o ajuda a criar aplicativos XML de alto desempenho.<br />-   Funciona com qualquer linguagem que pode usar bibliotecas de vínculo dinâmico (DLLs); recomendamos usar C++.|  
|[MSXML](https://msdn.microsoft.com/library/ms763742.aspx)|-   Tecnologia baseada em COM para processar o XML que vem incluído no sistema operacional Windows.<br />-   Fornece uma implementação nativa do DOM com suporte para XPath e XSLT.<br />-   Contém o analisador baseado em evento SAX2.|  
  
## <a name="see-also"></a>Consulte também

- [Processar dados XML usando o modelo DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
- [Processar dados XML usando o modelo de dados XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Compilador de XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
