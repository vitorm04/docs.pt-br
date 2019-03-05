---
title: Processamento de Dados XML na memória
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1a4587838180896b52bb79d447ed7ede3e22d1a
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836481"
---
# <a name="processing-xml-data-in-memory"></a>Processamento de Dados XML na memória
O Microsoft .NET Framework inclui três modelos para processar dados XML: as classes <xref:System.Xml.XmlDocument> e <xref:System.Xml.XPath.XPathDocument>, além de [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) e [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 A classe <xref:System.Xml.XmlDocument> implementa o núcleo de nível 1 do DOM (Modelo de Objeto de Documento) do W3C e as recomendações de nível 2 do DOM principal. O DOM é uma representação de árvore na memória (em cache) de um documento XML. Com o <xref:System.Xml.XmlDocument> e suas classes relacionadas, você pode criar documentos XML, carregar e acessar dados, modificar dados e salvar alterações.  
  
 A classe <xref:System.Xml.XPath.XPathDocument> é um repositório de dados somente leitura e na memória que é baseado no modelo de dados XPath. A classe <xref:System.Xml.XPath.XPathNavigator> oferece várias opções de edição e recursos de navegação usando um modelo de cursor em documentos XML contidos na classe <xref:System.Xml.XPath.XPathDocument> somente leitura bem como a classe <xref:System.Xml.XmlDocument>.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) é um modelo introduzido no .NET Framework versão 3.5 para processar dados XML. Ele é um modelo na memória que aproveita a [LINQ (consulta integrada à linguagem)](../../../csharp/programming-guide/concepts/linq/index.md). O LINQ estende a sintaxe da linguagem C# e Visual Basic para fornecer novos recursos de consulta.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Processar dados XML usando o modelo DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Discute o uso <xref:System.Xml.XmlDocument> e suas classes relacionadas para processar dados XML.  
  
 [Processar dados XML usando o modelo de dados XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Discute o uso das classes <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument> e <xref:System.Xml.XPath.XPathNavigator> para processar dados XML.  
  
 [Processar dados XML usando LINQ to XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Fornece uma visão geral do LINQ to XML e fornece links para a documentação do LINQ to XML.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Documentos e dados XML](../../../../docs/standard/data/xml/index.md)
