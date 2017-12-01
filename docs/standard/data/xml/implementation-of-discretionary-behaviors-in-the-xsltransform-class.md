---
title: "Implementação de comportamentos arbitrários na classe XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7b6c81a5737b879b7c1356c4b9c2ab68fbbc4688
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implementação de comportamentos arbitrários na classe XslTransform
> [!NOTE]
>  A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>. Consulte [usando a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [migrar da classe de XslTransform o](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para obter mais informações.  
  
 Os comportamentos arbitrários são descritos como os comportamentos listados na recomendação de versão 1,0 de transformações do World Wide Web Consortium (W3C) XSL (XSLT) (www.w3.org/TR/xslt), no qual o provedor de implementação escolher uma das várias opções possíveis como uma maneira de manipular uma situação. Por exemplo, em instruções de processamento criadoras da seção 7,3, a recomendação W3C informa que é um erro se criar uma instância do conteúdo de `xsl:processing-instruction` cria nós diferentes de nós de texto. Para alguns problemas, W3C informa o que a decisão deve ser feita se o processador decidir recuperar de erro. Para o problema da seção 7,3, o W3C com a implementação pode recuperar esse erro ignorando os nós e seu conteúdo.  
  
 Portanto, porque cada um dos comportamentos arbitrários permitidos pelo W3C, a tabela abaixo lista os comportamentos arbitrários implementados para a implementação de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] da classe de <xref:System.Xml.Xsl.XslTransform> , e que na seção recomendação W3C XSLT 1,0 que esse problema é discutido.  
  
|Problema|Comportamento|Seção|  
|-------------|--------------|-------------|  
|Um nó de texto corresponde `xsl:strip-space` e `xsl:preserve-space`.|Recupere|3.4|  
|Um nó de origem corresponde mais de uma regra de modelo.|Recupere|5.5|  
|Um namespace Uniform Resource Identifier (URI) é declarada para ser um alias para vários namespace URIs, tudo que tem o mesmo precedência de importação.|Recupere|7.1.1|  
|O nome do atributo em `xsl:attribute` e em `xsl:element` gerado de um modelo de valor de atributo não é um nome qualificado válido (QName).|Exceção lançada|7.1.2 e 7.1.3|  
|Adicionando um atributo a um elemento após os nós filho já foram adicionados ao nó do elemento.|Recupere|7.1.3|  
|Adicionando um atributo a algo diferente de um nó de elemento.|Recupere|7.1.3|  
|A instanciação do conteúdo de um elemento de `xsl:attribute` não é um nó de texto.|Recupere|7.1.3|  
|Dois conjuntos de atributo tem a mesma precedência de importação e nome expandido. Têm o mesmo atributo, e não há nenhum outro atributo definida que contém o atributo comum com o mesmo nome com importância mais alta.|Recupere|7.1.4|  
|o atributo de nome de`xsl:processing-instruction` não produz um nome de sem dois-pontos (NCName) e um destino de instrução de processamento.|Recupere|7.3|  
|Criar uma instância do conteúdo de `xsl:processing-instruction` cria nós diferentes de nós de texto.|Recupere|7.3|  
|Os resultados de criar uma instância do conteúdo de `xsl:processing-instruction` contêm a cadeia de caracteres “`?>`”.|Recupere|7.3|  
|Resultados de instanciar o conteúdo do `xsl:comment` contém a cadeia de caracteres "-", ou termina com "-".|Recupere|7.4|  
|Os resultados de criar uma instância do conteúdo de `xsl:comment` criar nós diferentes de nós de texto.|Recupere|7.4|  
|O modelo dentro de um elemento de variável associação retorna um nó de atributo ou um nó de namespace.|Recupere|11.2|  
|Há um erro que recupera o recurso URI passado na função do documento.|Exceção lançada|12.1|  
|A referência URI na função do documento contém um identificador de fragmento, e há um erro que processa o identificador do fragmento.|Exceção lançada|12.1|  
|Há vários atributos com o mesmo nome que não são nomeados `cdata-section-elements` em `xls:output`, e esses atributos têm a mesma precedência de importação.|Recupere|16|  
|O processador não oferece suporte ao valor de codificação de caracteres fornecido no atributo de `encoding` do elemento de `xsl:output` .|Recupere|16.1|  
|`disable-output-escaping` é usado para um nó de texto, e o nó de texto é usado para criar algo diferente de um nó de texto na árvore de resultado.|o atributo de`disable-output-escaping` é ignorado|16.4|  
|Convertendo uma árvore de resultado fragmente a um número ou cadeia se o fragmento da árvore de resultado contém um nó de texto com o escape de saída ativado.|Ignorado|16.4|  
|O escape de saída é desativado para os caracteres que não podem ser representados na codificação que o processador XSLT está usando para saída.|Ignorado|16.4|  
|Adicionando um nó de namespace para um elemento após os filhos lhe foram adicionados ou após os atributos lhe foram adicionados|Recupere|Erratas e25|  
|`xsl:number` é NaN, interminável, ou menor que 0,5.|Recupere|Erratas e24|  
|O segundo argumento nó- definida como a função do documento está vazia e a referência URI é relativo|Recupere|Erratas e14|  
  
 As seções de erratas podem ser encontradas em erratas de especificação de versão 1,0 de transformações do World Wide Web Consortium (W3C) XSL (XSLT), localizadas em www.w3.org/1999/11/REC-xslt-19991116-errata.  
  
## <a name="custom-defined-implementation-behaviors"></a>Comportamentos definidos de implementação personalizada  
 Há comportamentos exclusivos para a implementação da classe de <xref:System.Xml.Xsl.XslTransform> . Esta seção discutem a implementação específica do provedor de `xsl:sort` e recursos opcionais que são suportados pela classe de <xref:System.Xml.Xsl.XslTransform> .  
  
## <a name="xslsort"></a>xsl:sort  
 Ao usar uma transformação para classificar, a recomendação W3C XSLT 1,0 faça algumas observações. Elas são:  
  
-   Dois processadores XSLT podem ser processadores de conformação, mas ainda podem classificar diferente.  
  
-   Nem todos os processadores XSLT suportam os mesmos idiomas.  
  
-   Em relação aos processadores, linguagens diferentes podem variar em sua classificação em um idioma específico não especificado em `xsl:sort.`  
  
 A tabela a seguir mostra o comportamento de classificação implementado para cada tipo de dados na implementação do .NET Framework de uma transformação usando <xref:System.Xml.Xsl.XslTransform>.  
  
|Tipo de dados|Comportamento de classificação|  
|---------------|----------------------|  
|Texto|Os dados são classificados usando o método Common Language Runtime (CLR) String.Compare, e a localidade cultural. Quando o tipo de dados é igual a “texto”, classificação na classe de <xref:System.Xml.Xsl.XslTransform> se comporta de forma idêntica os comportamentos de comparação de cadeia de caracteres de CLR.|  
|Número|Os valores numéricos são tratados como números de idioma do caminho de XML (XPath) e classificados de acordo com os detalhes estruturados na recomendação de versão 1,0 do idioma de caminho W3C XML (XPath), seção 3,5 (www.w3.org/TR/xpath.html#numbers).|  
  
## <a name="optional-features-supported"></a>Recursos opcionais suportados  
 A tabela a seguir mostra os recursos que são opcionais para um processador XSLT implementa e é implementada na classe de <xref:System.Xml.Xsl.XslTransform> .  
  
|Recurso|Local de referência|Observações|  
|-------------|------------------------|-----------|  
|atributo de`disable-output-escaping` em `<xsl:text...>` e em marcas de `<xsl:value-of...>` .|Recomendação W3C XSLT, 1,0<br /><br /> Seção 16,4|O atributo de `disable-output-escaping` é ignorado quando os elementos de `xsl:text` ou de `xsl:value-of` são usados em `xsl:comment`, em `xsl:processing-instruction`, ou no elemento de `xsl:attribute` .<br /><br /> Os fragmentos da árvore de resultado que contêm texto e saída de texto que foram de escape não são suportados.<br /><br /> O atributo de escape é ignorado quando uma transformação a <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter> objetos.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Xsl.XslTransform>  
 [Classe XslTransform implementa do processador XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Transformações XSLT com a classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XPathNavigator nas transformações](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator nas transformações](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Entrada XPathDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Entrada de XmlDataDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Entrada de XmlDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
