---
title: XmlDataDocument inseriu a XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5c2fb203a1a6975d2b30e47528b15a9005a2583
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916019"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>XmlDataDocument inseriu a XslTransform
> [!NOTE]
> A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework 2.0. Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>. Confira [Usar a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para saber mais.  
  
 O Microsoft .NET Framework implementa o DOM (Modelo de Objeto do Documento) XML para fornecer acesso a dados em documentos XML e classes adicionais para leitura, gravação e navegação em documentos XML. <xref:System.Xml.XmlDataDocument>, localizado no espaço de <xref:System.Xml>, fornece acesso a dados relacional com sua capacidade para sincronizar com os dados relacionais em <xref:System.Data.DataSet>. Você pode exibir simultaneamente e manipular XML estruturada através da representação relacional de <xref:System.Data.DataSet> manipular XML ou semi-confiáveis estruturada através da representação DOM de <xref:System.Xml.XmlDataDocument>. Portanto <xref:System.Xml.XmlDataDocument> cruza os limites de XML e de mundos relacionais.  
  
 Se os dados são armazenados em uma estrutura relacional e você deseja que ele seja entrada para uma transformação XSLT, você pode carregar os dados relacionais em <xref:System.Data.DataSet> e associá-los com <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XPath.XPathNavigator>, entrada a <xref:System.Xml.Xsl.XslTransform>, é implementado em <xref:System.Xml.XmlDataDocument> através da interface de <xref:System.Xml.XPath.IXPathNavigable> . Colocando dados relacionais, carregando na <xref:System.Data.DataSet>, e usando sincronizar dentro de <xref:System.Xml.XmlDataDocument>, os dados relacionais agora podem ter as transformações XSLT executadas neles.  
  
 Para saber mais sobre como aplicar uma transformação de dados relacional, confira [Aplicando uma transformação XSLT a um conjunto de dados](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.XmlDataDocument>
- [Sincronização de DataSet e XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [Transformações XSLT com a classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [A classe XslTransform implementa o processador XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [XPathNavigator em transformações](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [XPathNodeIterator em transformações](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Entrada de XPathDocument para XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Entrada de XmlDocument para XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
