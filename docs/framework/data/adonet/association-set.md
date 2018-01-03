---
title: "conjunto de associações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5be982d25a4ab135d2b521b558e809b306b88230
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="association-set"></a>conjunto de associações
Um *conjunto de associações* é um contêiner lógico para [associação](../../../../docs/framework/data/adonet/association-type.md) instâncias do mesmo tipo. Um conjunto de associações não é um dados que modelam a compilação; isto é, não descreve a estrutura de dados ou relações. Em vez disso, um conjunto de associações fornece uma compilação para um ambiente de hospedagem ou de armazenamento (como Common Language Runtime ou um base de dados SQL Server) às instâncias de associação do grupo de modo que eles possam ser mapeadas em um armazenamento de dados.  
  
 Um conjunto de associação é definido dentro de um [contêiner de entidade](../../../../docs/framework/data/adonet/entity-container.md), que é um agrupamento lógico de [conjuntos de entidades](../../../../docs/framework/data/adonet/entity-set.md) e conjuntos de associação.  
  
 Uma definição de um conjunto de associações contém as informações a seguir:  
  
-   O nome de conjunto de associações. (Necessário)  
  
-   A associação de que irá conter instâncias. (Necessário)  
  
-   Dois [extremidades do conjunto de associação](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy`, e `WrittenBy`. Embora informações sobre conjuntos de associações não é transmitida no diagrama, o diagrama a seguir mostra um exemplo de conjuntos de associações e conjuntos de entidades baseados nesse modelo.  
  
 ![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 O exemplo a seguir mostra um conjunto de associações (`PublishedBy`) e dois conjuntos de entidades (`Books` e `Publishers`) com base no modelo conceitual mostrado acima. BI no `Books` conjunto de entidade representa uma ocorrência da `Book` tipo de entidade em tempo de execução. Da mesma forma, Pj representa um `Publisher` de instância de `Publishers` conjunto de entidades. BiPj representa uma ocorrência da `PublishedBy` associação no `PublishedBy` conjunto de associações.  
  
 ![Exemplo](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define um contêiner de entidade com um conjunto de associações para cada associação no diagrama anterior. Observe que o nome e a associação para cada conjunto de associações são definidos usando atributos XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 É possível definir vários conjuntos de associação por associação, contanto que nenhum compartilhamento de conjuntos de dois associação um [final do conjunto de associação](../../../../docs/framework/data/adonet/association-set-end.md). CSDL seguir define um contêiner de entidade com dois conjuntos de associações para associação de `WrittenBy` . Observe que os vários conjuntos de entidades foram definidos para os tipos de entidade de `Book` e de `Author` e que nenhum conjunto de associações compartilha fim do conjunto de associações.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Consulte também  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [propriedade de chave estrangeira](../../../../docs/framework/data/adonet/foreign-key-property.md)
