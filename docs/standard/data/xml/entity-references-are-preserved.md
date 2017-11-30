---
title: "Referências a entidades são preservadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 770c714e8f5942ea733c417ae9b06f69e4acf1a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-preserved"></a>Referências a entidades são preservadas
Quando a referência de entidade não é expandida, mas preservada, o modelo de objeto de documento (DOM) XML cria uma **XmlEntityReference** nó quando ele encontra uma referência de entidade.  
  
 Usando o seguinte XML,  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 o DOM cria um **XmlEntityReference** nó quando ele encontra a `&publisher;` referência. O **XmlEntityReference** contém nós filho copiados do conteúdo na declaração da entidade. O exemplo de código anterior contém texto na declaração da entidade, então um **XmlText** nó será criado como o nó filho do nó de referência de entidade.  
  
 ![Árvore de estrutura para referências de entidade preservadas](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Estrutura de árvore para as referências de entidade que são preservadas  
  
 Os nós filho do **XmlEntityReference** são criados a partir de nós de cópias de todos os filhos de **XmlEntity** nó quando a declaração de entidade foi encontrada.  
  
> [!NOTE]
>  Os nós copiados do **XmlEntity** nem sempre são cópias exatas de uma vez colocadas sob o nó de referência de entidade. Pode haver namespaces que estão no escopo no nó de referência de entidade, e que afetam a configuração final dos nós filho.  
  
 Por padrão, como entidades gerais `&abc;` são preservados e **XmlEntityReference** nós sempre criados.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
