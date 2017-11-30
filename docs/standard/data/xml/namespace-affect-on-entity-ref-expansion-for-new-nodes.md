---
title: "Afetar o namespace da expansão de referência de entidade para novos elementos e atributos recipiente de nós"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39110a9b44e6efbe7ad0331cfdb4fbe6078e7cfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Afetar o namespace da expansão de referência de entidade para novos elementos e atributos recipiente de nós
Porque o conteúdo de uma declaração de entidade pode conter qualquer coisa, há uma chance de que o conteúdo pode conter um elemento como `<!ENTITY aname "<elem>test</elem>">`.  
  
 Quando XML é analisado, `&aname;` não é expandido com o conteúdo de substituição em tempo de análise. A expansão XML não é feita porque a resolução de namespace para o elemento não pode ocorrer até que o nó é colocado no documento. Até esse momento, eles não há nenhum conhecimento de namespace que está no escopo. Quando o nó é colocado no documento, então a resolução do namespace ocorre, e o conteúdo de entidade resultante é analisado em seus nós apropriadas.  
  
> [!NOTE]
>  Uma vez que a expansão ocorre em um nó recém-criado de referência de entidade, nunca repete. Portanto, namespaces utilizados no texto de substituição para o elemento são associadas no momento em que o nó pai é definido. No entanto, o namespace pode ser alterado para nós de referência de entidade existentes quando você remove e inseri-los em outro lugar, ou em nós de referência de entidade são clonados com o **CloneNode** método.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
