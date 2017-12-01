---
title: Diretivas de folha de estilos inseridas em um documento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c5cfcc9f35e4a07e9426a4dd24c1e2f04985f16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Diretivas de folha de estilos inseridas em um documento
Ocasionalmente, existir XML contém a política de folha de estilos de `<?xml:stylesheet?>`. O Microsoft Internet Explorer aceita isso como uma alternativa para o `<?xml-stylesheet?>` sintaxe. Quando os dados XML contém uma diretiva de `<?xml:stylesheet?>` , conforme mostrado nos seguintes dados, tentando carregar esses dados no modelo de objeto de documento XML (DOM) palavras-chave acionar uma exceção.  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 Isso ocorre porque o `<?xml:stylesheet?>` é considerado inválido **instrução de processamento** ao DOM. Qualquer **instrução de processamento**, de acordo com os Namespaces na especificação XML, só podem ser nomes de dois-pontos não (NCNames), em vez de qualificado de nomes (QNames).  
  
 Na seção 6 de Namespaces na especificação do XML, o efeito de ter o **carga** e **LoadXml** métodos estão em conformidade com a especificação é que, em um documento:  
  
-   Todos os tipos de elemento e nomes de atributo contêm zero ou mais pontos.  
  
-   Nenhum nome de entidade, destino de ProcessingInstruction, ou nome de notação contém todos os dois-pontos.  
  
 Com `<?xml:stylesheet?>` que contém dois-pontos, você agora viola a regra no segundo marcador.  
  
 De acordo com o World Wide Web Consortium (W3C) que associa folhas de estilo com a recomendação de versão 1,0 de documentos XML, localizado em www.w3.org/TR/xml-stylesheet, a instrução de processamento para associar uma folha de estilos XSLT com um documento XML é `<?xml-stylesheet?>`, com um sublinhado que substitui o separador dois-pontos.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
