---
title: Resolvendo folhas de estilos XSLT e documentos externos
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39e8afd8c22ca757141d2a7b556b115f8380e731
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48847484"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Resolvendo folhas de estilos XSLT e documentos externos
Há várias vezes durante uma transformação quando você precise resolver recursos externos.  
  
> [!NOTE]
>  A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 Há várias vezes durante uma transformação quando você precise resolver recursos externos:  
  
-   Durante <xref:System.Xml.Xsl.XslTransform.Load%2A> para localizar uma folha de estilos externa.  
  
-   Durante <xref:System.Xml.Xsl.XslTransform.Load%2A> para resolver alguns elementos de `<xsl:include>` ou de `<xsl:import>` localizados na folha de estilos.  
  
-   Durante <xref:System.Xml.Xsl.XslTransform.Transform%2A> para resolver algumas funções de `document()` .  
  
## <a name="using-the-xmlresolver-class"></a>Usando a classe de XmlResolver  
 Se a autenticação for necessária para acessar um recurso de rede, use os métodos de <xref:System.Xml.Xsl.XslTransform.Load%2A> que têm um parâmetro de <xref:System.Xml.XmlResolver> para passar o objeto de <xref:System.Xml.XmlResolver> , que tem as propriedades credenciais necessárias definidas.  
  
 Se você tiver <xref:System.Xml.XmlResolver> personalizado que você deseja usar, ou se você precisar especificar credenciais diferentes, a tabela a seguir lista a tarefa necessária, como quando o recurso externo precisar a resolução.  
  
|Processo requer que a resolução|Tarefa necessária|  
|--------------------------------------|-------------------|  
|Durante <xref:System.Xml.Xsl.XslTransform.Load%2A> para localizar a folha de estilos.|Especificar o método sobrecarregado de <xref:System.Xml.Xsl.XslTransform.Load%2A> que aceita, como um parâmetro, <xref:System.Xml.XmlResolver> se a folha de estilos é um recurso que requer credenciais.|  
|Durante <xref:System.Xml.Xsl.XslTransform.Load%2A> para resolver `<xsl:include>` ou `<xsl:import>`.|Especificar o método sobrecarregado de <xref:System.Xml.Xsl.XslTransform.Load%2A> que aceita, como um parâmetro, <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> é usado para carregar as folhas de estilos referenciadas pelas declarações de `import` ou de `include` . Se você passar em `null`, os recursos externos não são resolvidos.|  
|Durante uma transformação resolver qualquer `document()` funciona.|Especifique <xref:System.Xml.XmlResolver> durante a transformação usando o método <xref:System.Xml.Xsl.XslTransform.Transform%2A> que recebe um argumento de <xref:System.Xml.XmlResolver>.|  
  
 A função `document()` recupera outros recursos XML de uma folha de estilos, além dos dados XML iniciais fornecidos pelo fluxo de entrada. Já que essa função permite a inclusão de dados XML que podem ser encontrados em outro lugar, <xref:System.Xml.XmlResolver> com um valor de `null` fornecido para o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> impede que a função de `document()` executar. Se você desejar usar a função de `document()` , use o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> que leva <xref:System.Xml.XmlResolver> como um parâmetro, além de ter o conjunto de permissões apropriado.  
  
 Para obter mais informações sobre o método de <xref:System.Xml.Xsl.XslTransform.Load%2A> e o uso de <xref:System.Xml.XmlResolver>, consulte <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Quando o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> é chamado, as permissões são calculadas com a evidência fornecida em tempo de carregamento, e esse conjunto de permissões é atribuído ao processo inteiro de transformação. Se a função de `document()` tentar iniciar uma ação que requer permissões não encontradas no dataset, uma exceção é lançada.  
  
## <a name="see-also"></a>Consulte também

- [Transformações XSLT com a classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [A classe XslTransform implementa o processador XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [Saída de um XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
- [Transformações XSLT em diferentes repositórios](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
- [XsltArgumentList para parâmetros de folha de estilos e objetos de extensão](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
- [Scripts de folha de estilos de XSLT usando \<<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
- [Suporte à função msxsl:node-set()](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
- [XPathNavigator em transformações](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [XPathNodeIterator em transformações](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [Entrada de XPathDocument para XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [Entrada de XmlDataDocument para XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [Entrada de XmlDocument para XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
