---
title: "Criando novos referências a entidades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22e9b66f58275141cf9da154573ca43a0b90affc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-entity-references"></a>Criando novos referências a entidades
O **CreateEntityReference** método cria um novo **XmlEntityReference** nó. O modelo de objeto de documento XML (DOM) parece para ver se o nome de entidade que está sendo referenciado foi declarado. Em caso afirmativo, os nós filho de **XmlEntityReference** nó são copiados a partir do nó de declaração de entidade. Se não houver nenhuma declaração de entidade que corresponde, um nó vazia de texto é anexado como o único filho do nó de referência de entidade. Porque os nós filho do **XmlEntityReference** nó são cópias de outros nós, esses nós filho são somente leitura e não podem ser modificados.  
  
 Quando os nós são copiados, pode haver namespace no escopo na referência de entidade. Este namespace afeta a configuração de qualquer elemento ou nós de atributo gerado.  
  
> [!NOTE]
>  O DOM adiciona nós filho para o **EntityReference** somente quando você insere o **EntityReference** nó no documento. Recém-criado **EntityReference** nós ter nenhum nó filho.  
  
 Embora o **XmlDataDocument** é uma classe derivada do **XmlDocument**, o **XmlDataDocument** não oferece suporte à criação de referências de entidade. Isso ocorre porque **EntityReference** filhos são somente leitura. Os filhos de um **EntityReference** nó pode abranger mais de uma região. Nesse caso, parte de uma linha associada com a região que contém uma parte de um **EntityReference** serão somente leitura.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
