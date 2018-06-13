---
title: Diretivas de folha de estilos inseridas em um documento
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa671304c611db571b160cd1d960b83bf451c9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569323"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Diretivas de folha de estilos inseridas em um documento
Ocasionalmente, existir XML contém a política de folha de estilos de `<?xml:stylesheet?>`. O Microsoft Internet Explorer aceita isso como uma alternativa à sintaxe `<?xml-stylesheet?>`. Quando os dados XML contém uma diretiva de `<?xml:stylesheet?>` , conforme mostrado nos seguintes dados, tentando carregar esses dados no modelo de objeto de documento XML (DOM) palavras-chave acionar uma exceção.  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 Isso ocorre porque `<?xml:stylesheet?>` é considerado um **ProcessingInstruction** inválido para DOM. Qualquer **ProcessingInstruction**, de acordo com os namespaces na especificação XML, só pode ser nomes de sem dois-pontos (NCNames), diferentemente de nomes qualificados (QNames).  
  
 Conforme a seção 6 de Namespaces na especificação XML, o efeito de fazer os métodos **Load** e **LoadXml** obedecerem à especificação é que, em um documento:  
  
-   Todos os tipos de elemento e nomes de atributo contêm zero ou mais pontos.  
  
-   Nenhum nome de entidade, destino de ProcessingInstruction, ou nome de notação contém todos os dois-pontos.  
  
 Com `<?xml:stylesheet?>` que contém dois-pontos, você agora viola a regra no segundo marcador.  
  
 De acordo com o World Wide Web Consortium (W3C) que associa folhas de estilo com a recomendação de versão 1,0 de documentos XML, localizado em www.w3.org/TR/xml-stylesheet, a instrução de processamento para associar uma folha de estilos XSLT com um documento XML é `<?xml-stylesheet?>`, com um sublinhado que substitui o separador dois-pontos.  
  
## <a name="see-also"></a>Consulte também  
 [DOM (Modelo de Objeto do Documento) de XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
