---
title: "Transformações XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d7fa8492487daff68fd8ebaf4159dd537d13e51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-transformations"></a>Transformações XSLT
A linguagem XSL Transformation (XSLT) permite transformar o conteúdo de um documento XML de origem em outro documento que seja diferente no formato ou estrutura. Por exemplo, você pode usar XSLT para transformar XML em HTML para usar em um site ou para transformá-lo em um documento que contém somente os campos exigidos por um aplicativo. Esse processo de transformação é especificado pelo [recomendação do W3C XSLT (transformações XSL) versão 1.0](http://go.microsoft.com/fwlink/?LinkID=49919).  
  
 A classe <xref:System.Xml.Xsl.XslCompiledTransform> é o processador XSLT no .NET Framework. A classe <xref:System.Xml.Xsl.XslCompiledTransform> oferece suporte à recomendação XSLT 1.0 do W3C.  
  
> [!NOTE]
>  A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework versão 2.0. A classe <xref:System.Xml.Xsl.XslCompiledTransform> é uma nova implementação do mecanismo do XSLT. Ela inclui aprimoramentos de desempenho e novos recursos de segurança. A prática recomendada é criar aplicativos do XSLT usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Usando a classe de XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 [Migrando da classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Aborda como migrar o código da classe <xref:System.Xml.Xsl.XslTransform>.  
  
 [Compilador XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 Fornece informações sobre como usar o compilador do XSLT.  
  
 [Transformações XSLT com a classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 Fornece informações sobre como usar a classe <xref:System.Xml.Xsl.XslTransform>.  
  
 **Observação** o <xref:System.Xml.Xsl.XslTransform> classe está obsoleta na versão do .NET Framework 2.0.  
  
## <a name="reference"></a>Referência  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Documentos e dados XML](../../../../docs/standard/data/xml/index.md)
