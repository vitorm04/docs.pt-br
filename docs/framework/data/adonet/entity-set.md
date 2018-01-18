---
title: conjunto de entidades
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 050c73d3fd9146c8eee83baf1bd504acc18c8718
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-set"></a>conjunto de entidades
Um *conjunto de entidades* é um contêiner lógico para instâncias de um [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) e instâncias de qualquer tipo derivado desse tipo de entidade. (Para obter informações sobre tipos derivados, consulte [modelo de dados de entidade: herança](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) A relação entre um tipo de entidade e um conjunto de entidades é análoga a relação entre uma linha e uma tabela em uma base de dados relacional: Como uma linha, um tipo de entidade descreve a estrutura de dados, e, como uma tabela, um conjunto de entidades contém instâncias de uma estrutura fornecida. Um conjunto de entidades não é um dados que modelam a compilação; não descreve a estrutura de dados. Em vez disso, um conjunto de entidades fornece uma compilação para um ambiente de hospedagem ou de armazenamento (como Common Language Runtime ou um base de dados do SQL Server) instâncias de tipo de entidade do grupo de modo que eles possam ser mapeadas em um armazenamento de dados.  
  
 Um conjunto de entidades é definido dentro de um [contêiner de entidade](../../../../docs/framework/data/adonet/entity-container.md), que é um agrupamento lógico de conjuntos de entidades e [AssociationSets](../../../../docs/framework/data/adonet/association-set.md).  
  
 Para uma instância do tipo de entidade existe em um conjunto de entidades, o seguinte deve ser verdadeira:  
  
-   O tipo de qualquer instância é o mesmo como o tipo de objeto no qual o conjunto de entidades é baseado, ou o tipo de instância é um subtipo do tipo de objeto.  
  
-   O [chave da entidade](../../../../docs/framework/data/adonet/entity-key.md) para a instância é exclusiva dentro do conjunto de entidade.  
  
-   A instância não existir em qualquer outro conjunto de entidades.  
  
    > [!NOTE]
    >  Os vários conjuntos de entidades podem ser definidos usando o mesmo tipo de entidade, mas uma instância de um tipo de dado entidade só pode existir em um conjunto de entidades.  
  
 Você não precisa definir um conjunto de entidades para cada tipo de entidade em um modelo conceitual.  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.  
  
 ![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 A seguir temos de diagrama dois conjuntos de entidades (`Books` e `Publishers`) e um conjunto de associações (`PublishedBy`) com base no modelo conceitual mostrado acima. BI no `Books` conjunto de entidade representa uma ocorrência da `Book` tipo de entidade em tempo de execução. Da mesma forma, Pj representam um `Publisher` de instância de `Publishers` conjunto de entidades. BiPj representa uma ocorrência da `PublishedBy` associação no `PublishedBy` conjunto de associações.  
  
 ![Exemplo](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define um contêiner de entidade com um conjunto de entidades para cada tipo de entidade no modelo conceitual mostrado acima. Observe que o nome e o tipo de entidade para cada conjunto de entidades são definidos usando atributos XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 É possível definir vários conjuntos de entidades por tipo (MEST). CSDL seguir define um contêiner de entidade com dois conjuntos de entidades para o tipo de entidade de `Book` :  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Consulte também  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
