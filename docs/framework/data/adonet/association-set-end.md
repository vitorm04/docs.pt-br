---
title: "extremidade do conjunto de associação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 20810eddda98403d244f6104807504489dde71cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="association-set-end"></a>extremidade do conjunto de associação
Um *final do conjunto de associação* identifica o [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) e [conjunto de entidades](../../../../docs/framework/data/adonet/entity-set.md) no final de um [conjunto de associações](../../../../docs/framework/data/adonet/association-set.md). Termina do conjunto de associações são definidas como parte de um conjunto de associações; um conjunto de associações deve ter exatamente duas termina do conjunto de associações.  
  
 Uma definição de final do conjunto de associações contém as informações a seguir:  
  
-   Um dos tipos de entidade envolvidos no conjunto de associações. (Necessário)  
  
-   O conjunto de entidades para o tipo de entidade envolvido no conjunto de associações. (Necessário)  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com duas associações: `WrittenBy` e `PublishedBy`.  
  
 ![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 O diagrama a seguir mostra um conjunto de associações (`PublishedBy`) e dois conjuntos de entidades (`Books` e `Publishers`) com base no modelo conceitual mostrado acima. Termina do conjunto de associações são conjuntos de entidades de `Books` e de `Publishers` . BI no `Books` conjunto de entidade representa uma ocorrência da `Book` tipo de entidade em tempo de execução. Da mesma forma, Pj representa um `Publisher` de instância de `Publishers` conjunto de entidades. BiPj representa uma ocorrência da `PublishedBy` associação no `PublishedBy` conjunto de associações.  
  
 ![Exemplo](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma DSL chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define um contêiner de entidade com um conjunto de associações para cada associação no diagrama anterior. Observe que termina do conjunto de associações são definidas como parte de cada definição do conjunto de associações.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos chave do modelo de dados de entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de dados de entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
