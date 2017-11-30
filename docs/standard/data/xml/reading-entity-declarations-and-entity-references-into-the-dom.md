---
title: "Declarações de entidade de leitura e referências a entidades em DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6370db06cbe7ff8d46258b0315059f5c37587fea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Declarações de entidade de leitura e referências a entidades em DOM
Uma entidade é uma declaração que indica um nome ser usado em XML no lugar do conteúdo ou marcação. Há duas partes a entidades. Primeiro, você deve a um nome ao conteúdo de substituição utilizando uma declaração de entidade. Uma declaração de entidade é criada usando a sintaxe de `<!ENTITY name "value">` em um Document type definition (DTD) ou no esquema XML. Em segundo lugar, o nome definido na declaração de entidade é usado posteriormente em XML. Quando usado em XML, é chamado uma referência de entidade. Por exemplo, a seguinte declaração de entidade declara uma entidade de nome `publisher` que está sendo associado com o conteúdo de “de pressionamento Microsoft”.  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 O exemplo a seguir mostra o uso dessa declaração de entidade em XML como uma referência de entidade.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Alguns analisadores expandem automaticamente entidades quando um documento é carregado na memória. Portanto, quando XML está sendo lido na memória, as declarações de entidade são recordadas e salvas. Quando o analisador encontra posteriormente os caracteres de `&;` , que identifica uma referência de entidade geral, o analisador pesquisa que nome em uma tabela da declaração de entidade. A referência, `&publisher;` é substituído pelo conteúdo que representa. Usando o seguinte XML,  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 expanda a referência de entidade e substituir `&publisher;` com o conteúdo da Microsoft oferece seguinte XML expandido.  
  
 **Saída**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Há muitos tipos das entidades. O diagrama a seguir mostra a divisão dos tipos de entidade e da terminologia.  
  
 ![Fluxograma da hierarquia de tipo de entidade](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 O padrão para a implementação do Microsoft .NET Framework do XML DOM Document Object Model () é preservar as referências de entidades e expandir as entidades quando o XML é carregado. A implicação é que um documento é carregado no DOM, um **XmlEntityReference** nó que contém a variável de referência `&publisher;` é criada, conosco filho que representa o conteúdo da entidade declarada no DTD.  
  
 Usando o `<!ENTITY publisher "Microsoft Press">` declaração de entidade, o diagrama a seguir mostra o **XmlEntity** e **XmlText** nós criados a partir dessa declaração.  
  
 ![nós criados na declaração de entidade](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 As diferenças quando as referências a entidades são expandidos e quando não são faz uma diferença no qual nós são gerados na árvore DOM, na memória. A diferença em nós que são gerados é explicada nos tópicos [referências a entidades são preservadas](../../../../docs/standard/data/xml/entity-references-are-preserved.md) e [referências a entidades são expandidos e não preservadas](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
