---
title: "Referências a entidades são expandidos e não preservadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 069d3b94a0269917400e75fdbe975ec39dcfdb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Referências a entidades são expandidos e não preservadas
Quando a referência de entidade é expandida e substituída pelo texto representa, o **XmlEntityReference** nó não é criado. Em vez disso, a declaração de entidade é analisada e nós criados do conteúdo na declaração são copiados em vez do **XmlEntityReference**. Portanto, o `&publisher;` exemplo, o `&publisher;` não for salva, mas em vez disso, um **XmlText** nó será criado.  
  
 ![expandido a estrutura de árvore](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Estrutura de árvore para as referências de entidade que são expandidas  
  
 As entidades de caractere como `B` ou `<` não são preservados. Em vez disso, sempre são expandidos e representados como nós de texto.  
  
 Para preservar **XmlEntityReference** nós e nós filho da referência de entidade anexado a ele, defina o **EntityHandling** sinalizador como **ExpandCharEntities**. Caso contrário, deixe o **EntityHandling** sinalizador padrão, que é **ExpandEntities**. Nesse caso, você não verá nós de referência de entidade em DOM. Os nós são substituídos pelos nós que são cópias dos nós filho da declaração de entidade.  
  
 Um efeito colateral de não preservar referências a entidades é que quando o documento é salvo e passado sobre a outro aplicativo, o aplicativo de receptor não sabe que os nós foram gerados por uma referência de entidade. No entanto, quando as referências a entidades são preservadas, um aplicativo de receptor considera uma referência de entidade e ler os nós filho. É aparente que os nós filhos representam informações que estava na declaração de entidade. Por exemplo, os DOM têm teoricamente a seguinte estrutura se as referências a entidades são preservadas.  
  
 XmlElement: editor  
  
 XmlEntityReference: `&publisher;`  
  
 XmlText: Pressione da Microsoft  
  
 Se as referências a entidades são expandidas em DOM, que é o método padrão, a estrutura tem esse tipo de árvore:  
  
 XmlElement: editor  
  
 XmlText: Pressione da Microsoft  
  
 Observe que o nó de referência de entidade será excluído e o aplicativo de recebimento não pode determinar que o **XmlText** nó que contém "Microsoft Press" foi criado a partir de uma declaração de entidade.  
  
 Se você usar um leitor que não é possível resolver entidades, o **carga** método lançará uma exceção quando ele encontra uma referência de entidade.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
