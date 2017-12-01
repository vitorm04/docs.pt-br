---
title: "Transformações XSLT com a classe XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 619e37ab63735ea77d3afb0d94f284b2f310efc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a>Transformações XSLT com a classe XslTransform
> [!NOTE]
>  A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>. Consulte [usando a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [migrar da classe de XslTransform o](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para obter mais informações.  
  
 O objetivo do XSLT é transformar o conteúdo de um documento XML de origem em outro documento que seja diferente no formato ou estrutura (por exemplo, para transformar XML em HTML para uso em um site ou para transformá-lo em um documento que contém somente os campos exigidos por um aplicativo). Esse processo de transformação é especificado pela recomendação XSLT World Wide Web Consortium (W3C) versão 1.0 localizada em www.w3.org/TR/xslt. No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], a classe <xref:System.Xml.Xsl.XslTransform>, localizada no namespace <xref:System.Xml.Xsl> é o processador XSLT que implementa a funcionalidade dessa especificação. Há um pequeno número de recursos que não foram implementados de recomendação do W3C XSLT 1.0, listada em [saída de um XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md). A figura a seguir mostra a arquitetura de transformação do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="overview"></a>Visão Geral  
 ![Arquitetura de transformação XSLT](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")  
Arquitetura de transformação  
  
 A recomendação XSLT usa a linguagem XPath para selecionar partes de um documento XML, onde XPath é uma linguagem de consulta usada para navegar em nós de uma árvore do documento. Conforme mostrado no diagrama, a implementação de XPath do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] é usada para selecionar partes de XML armazenadas em várias classes, como um <xref:System.Xml.XmlDocument>, um <xref:System.Xml.XmlDataDocument> e um <xref:System.Xml.XPath.XPathDocument>. Um <xref:System.Xml.XPath.XPathDocument> é um repositório de dados XSLT otimizado e, quando usado com <xref:System.Xml.Xsl.XslTransform>, fornece transformações XSLT com bom desempenho.  
  
 A seguinte tabela lista classes geralmente usadas ao trabalhar com o <xref:System.Xml.Xsl.XslTransform> e XPath e sua função.  
  
|Classe ou interface|Função|  
|------------------------|--------------|  
|<xref:System.Xml.XPath.XPathNavigator>|É uma API que fornece um modelo de estilo de cursor para navegar em um repositório, junto com suporte a consulta XPath. Não fornece a edição do repositório subjacente. Para editar, use a classe <xref:System.Xml.XmlDocument>.|  
|<xref:System.Xml.XPath.IXPathNavigable>|É uma interface que fornece um método `CreateNavigator` para um <xref:System.Xml.XPath.XPathNavigator> para o repositório.|  
|<xref:System.Xml.XmlDocument>|Ela permite a edição deste documento. Implementa <xref:System.Xml.XPath.IXPathNavigable>, permitindo os cenários de edição de documento onde as transformações XSLT são necessárias posteriormente. Para obter mais informações, consulte [entrada XmlDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).|  
|<xref:System.Xml.XmlDataDocument>|É derivada do <xref:System.Xml.XmlDocument>. Ela faz a ponte sobre os mundos relacionais e XML usando <xref:System.Data.DataSet> para otimizar o armazenamento de dados estruturados dentro do documento XML de acordo com mapeamentos especificados no <xref:System.Data.DataSet>. Ela implementa <xref:System.Xml.XPath.IXPathNavigable>, permitindo situações onde as transformações XSLT podem ser executadas sobre os dados relacionais recuperados de um banco de dados. Para obter mais informações, consulte [integração XML com dados relacionais e ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).|  
|<xref:System.Xml.XPath.XPathDocument>|Essa classe é otimizada para processamento de <xref:System.Xml.Xsl.XslTransform> e consultas XPath, e fornece um cache somente leitura de alto desempenho. Implementa <xref:System.Xml.XPath.IXPathNavigable> e é o repositório preferido a ser usado para transformações XSLT.|  
|<xref:System.Xml.XPath.XPathNodeIterator>|Fornece a navegação em conjuntos de nós XPath. Todos os métodos de seleção XPath no <xref:System.Xml.XPath.XPathNavigator> retornam um <xref:System.Xml.XPath.XPathNodeIterator>. Vários objetos <xref:System.Xml.XPath.XPathNodeIterator> podem ser criados no mesmo repositório, cada um representando um conjunto de nós selecionado.|  
  
## <a name="msxml-xslt-extensions"></a>Extensões de MSXML XSLT  
 As funções `msxsl:script` e `msxsl:node-set` são as únicas extensões XSLT do Microsoft XML Core Services (MSXML) com suporte pela classe <xref:System.Xml.Xsl.XslTransform>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir carrega uma folha de estilos XSLT, lê um arquivo chamado mydata.xml em um <xref:System.Xml.XPath.XPathDocument> e executa uma transformação nos dados em um arquivo fictício chamado myStyleSheet.xsl, enviando a saída formatada para o console.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
    Private filename As [String] = "mydata.xml"  
    Private stylesheet As [String] = "myStyleSheet.xsl"  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load(stylesheet)  
        Dim xpathdocument As New XPathDocument(filename)  
        Dim writer As New XmlTextWriter(Console.Out)  
        writer.Formatting = Formatting.Indented  
  
        xslt.Transform(xpathdocument, Nothing, writer, Nothing)  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample   
{  
    private const String filename = "mydata.xml";  
    private const String stylesheet = "myStyleSheet.xsl";  
  
    public static void Main()   
    {  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
    XPathDocument xpathdocument = new  
    XPathDocument(filename);  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting=Formatting.Indented;  
  
    xslt.Transform(xpathdocument, null, writer, null);      
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Xsl.XslTransform>  
 [Classe XslTransform implementa do processador XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Implementação de comportamentos arbitrários na classe XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
 [XPathNavigator nas transformações](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator nas transformações](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Entrada XPathDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Entrada de XmlDataDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Entrada de XmlDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
