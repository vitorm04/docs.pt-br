---
title: Documentos e dados XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1edd267ed388f630cc332caa278d5c47a40d77d5
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835116"
---
# <a name="xml-documents-and-data"></a>Documentos e dados XML
O .NET Framework fornece um conjunto de classes abrangente e integrado que permite que você crie aplicativos com reconhecimento de XML facilmente. As classes nos namespaces a seguir suportam a análise e gravação de XML, edição de dados XML na memória, validação de dados e transformação de XSLT.  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 Para obter uma lista completa, pesquise "System.Xml" no [navegador da API .NET](https://docs.microsoft.com/dotnet/api/?term=system.xml).  
  
 As classes nesses namespaces suportam recomendações World Wide Web Consortium (W3C). Por exemplo:  
  
-   A classe <xref:System.Xml.XmlDocument?displayProperty=nameWithType> implementa as recomendações do [DOM (Modelo de Objeto do Documento) Core do W3C nível 1](https://www.w3.org/TR/REC-DOM-Level-1/) e do [DOM Core nível 2](https://www.w3.org/TR/DOM-Level-2-Core/).  
  
-   As classes <xref:System.Xml.XmlReader?displayProperty=nameWithType> e <xref:System.Xml.XmlWriter?displayProperty=nameWithType> dão suporte para as recomendações [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) e [Namespaces em XML](https://www.w3.org/TR/REC-xml-names/).  
  
-   Os esquemas na classe <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> dão suporte às recomendações [XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) (Esquema XML Parte 1: Estruturas) e [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) (Esquema XML Parte 2: Tipos de dados) do W3C.  
  
-   As classes no namespace <xref:System.Xml.Xsl?displayProperty=nameWithType> dão suporte para as transformações XSLT que estão em conformidade com a recomendação [W3C XSLT 1.0](https://www.w3.org/TR/xslt).  
  
 As classes XML do .NET Framework fornecem esses benefícios:  
  
-   **Produtividade.** O [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) e o [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) facilitam a programação com XML e fornecem uma experiência de consulta que é semelhante ao SQL.  
  
-   **Extensibilidade.** As classes XML no .NET Framework são extensíveis pelo uso de classes base abstratas e métodos virtuais. Por exemplo, você pode criar uma classe derivada da classe de <xref:System.Xml.XmlUrlResolver> que armazena o fluxo de cache no disco local.  
  
-   **Arquitetura conectável.** O .NET Framework fornece uma arquitetura na qual os componentes podem se utilizar uns aos outros e os dados podem ser transmitidos entre os componentes. Por exemplo, um armazenamento de dados, tal como um objeto <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>, pode ser transformado com a classe <xref:System.Xml.Xsl.XslCompiledTransform> e a saída pode então ser transmitida para outro armazenamento ou retornados como um fluxo de um serviço da web.  
  
-   **Desempenho.** Para melhorar o desempenho do aplicativo, algumas das classes XML do .NET Framework dão suporte a um modelo baseado em streaming com as seguintes características:  
  
    -   Armazenamento em cache mínimo para somente encaminhamento, análise de recepção modelo (<xref:System.Xml.XmlReader>).  
  
    -   Validação somente de encaminhamento (<xref:System.Xml.XmlReader>).  
  
    -   Navegação do cursor que minimiza a criação do nó com um único nó virtual no entanto fornece acesso aleatório ao documento (<xref:System.Xml.XPath.XPathNavigator>).  
  
     Para obter um melhor desempenho sempre que o processamento de XSLT for necessário, você pode usar a classe <xref:System.Xml.XPath.XPathDocument>, que é um repositório otimizado, somente de leitura para consultas do XPath projetado para trabalhar com eficiência com a classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   **Integração com o ADO.NET.** As classes XML e o [ADO.NET](../../../../docs/framework/data/adonet/index.md) são bem integrados para reunir dados relacionais e XML. A classe de <xref:System.Data.DataSet> é um cache de memória dos dados recuperados de uma base de dados. A classe <xref:System.Data.DataSet> tem a capacidade de ler e escrever XML usando as classes de <xref:System.Xml.XmlReader> e de <xref:System.Xml.XmlWriter> , para manter sua estrutura de esquema relacional como esquemas XML (XSD), e para interpretar a estrutura do esquema de um documento XML.  
  
## <a name="in-this-section"></a>Nesta seção  
 [XML Processing Options](../../../../docs/standard/data/xml/xml-processing-options.md) (Opções de processamento de XML)  
 Discute opções para processar dados XML.  
  
 [Processing XML Data In-Memory](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) (Processamento de dados XML na memória)  
 Discute os três modelos para processar dados XML na memória: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) e [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), a classe <xref:System.Xml.XmlDocument> (com base no Modelo de Objeto do Documento do W3C) e a classe <xref:System.Xml.XPath.XPathDocument> (com base no modelo de dados do XPath).  
  
 [Transformações XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 Descreve como usar o processador XSLT.  
  
 [XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md) [SOM (Modelo de Objeto de Esquema) XML]  
 Descreve as classes usadas para criar e manipular esquemas XML (XSD), fornecendo uma classe <xref:System.Xml.Schema.XmlSchema> para carregar e editar um esquema.  
  
 [XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md) (Integração XML com os dados relacionais e o ADO.NET)  
 Descreve como o .NET Framework habilita o acesso síncrono, em tempo real, às representações de dados relacionais e hierárquicas através dos objetos <xref:System.Data.DataSet> e <xref:System.Xml.XmlDataDocument>.  
  
 [Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md) (Gerenciando namespaces em um documento XML)  
 Descreve como a classe <xref:System.Xml.XmlNamespaceManager> classe é usada para armazenar e manter as informações do namespace.  
  
 [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md) (Suporte a tipo nas classes System.XML)  
 Descreve como mapa de tipos de dados XML para tipos de CLR, como converter tipos de dados XML e outros recursos de suporte de tipo nas classes <xref:System.Xml>.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 Fornece informações sobre como acessar dados usando ADO.NET.  
  
 [Segurança](../../../../docs/standard/security/index.md)  
 Fornece uma visão geral do sistema de segurança do .NET Framework.  
  
