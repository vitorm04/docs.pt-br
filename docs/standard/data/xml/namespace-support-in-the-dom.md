---
title: Suporte do namespace em DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3145df6517df9db580bfcc5d67edd9d1a61f290b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-support-in-the-dom"></a>Suporte do namespace em DOM
O modelo de objeto (DOM) de documento XML é completamente URL ciente. Somente os documentos XML URL cientes são suportados. World Wide Web Consortium (W3C) especifica que os aplicativos DOM que o nível de implementar 1 pode estar ciente não-namespace-, e os recursos do nível 2 DOM são cientes URL. No entanto, todos os recursos em DOM XML são cientes URL, indiferente se o método é recomendação DOM nível de nível 1 ou 2.  
  
 Por exemplo, em uma configuração não-namespace- ciente, a chamada `setAttribute("A:b", "123")`, conforme especificado na recomendação de nível 1 DOM, não resulta em um atributo com um prefixo de `A` e um nome local de `b`. Resultaria em um atributo com o valor `A:b`.  
  
 Em um ambiente URL ciente, na chamada a resultados de `setAttribute("A:b", "123")` de nível 2 DOM em um atributo com um prefixo de `A` e um nome local de `b`. Isso é como funciona o DOM do Microsoft .NET Framework.  
  
 Portanto, para todos os métodos que têm um parâmetro de nome, esses métodos também têm um prefixo para qualificar o nome. O parâmetro de nome, como o `A:b` no **setAttribute** método DOM nível 1, é analisado da seguinte maneira:  
  
-   Se não houver nenhum caractere dois-pontos (:), então o nome local é definido para o parâmetro de `name` , e o prefixo e o NamespaceURI são cadeias de caracteres vazias.  
  
-   Se um dois-pontos é encontrado, o nome é dividido em duas partes com base na posição do primeiro caractere dois-pontos. O prefixo é definido para a cadeia de caracteres encontrada antes de pontos, e o nome local é definido para a cadeia de caracteres encontrada após os dois-pontos. Para os métodos que não têm um valor de NamespaceURI, o NamespaceURI não é resolvido e o não são definidas para a cadeia de caracteres vazia. Caso contrário, o NamespaceURI é definido para a cadeia de caracteres passada para o método. Se o prefixo for indefinido, o **salvar** método e **InnerXml** e **OuterXml** propriedades falhar.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
