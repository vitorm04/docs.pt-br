---
title: conjunto de associações
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 58d8794a21cc37ab84386c820b192fb29946095c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153424"
---
# <a name="association-set"></a>conjunto de associações

Um *conjunto de associação* é um contêiner lógico para instâncias de [Associação](association-type.md) do mesmo tipo. Um conjunto de associações não é um dados que modelam a compilação; isto é, não descreve a estrutura de dados ou relações. Em vez disso, um conjunto de associações fornece uma compilação para um ambiente de hospedagem ou de armazenamento (como Common Language Runtime ou um base de dados SQL Server) às instâncias de associação do grupo de modo que eles possam ser mapeadas em um armazenamento de dados.  
  
 Um conjunto de associação é definido em um [contêiner de entidade](entity-container.md), que é um agrupamento lógico de conjuntos de [entidades](entity-set.md) e conjuntos de associação.  
  
 Uma definição de um conjunto de associações contém as informações a seguir:  
  
- O nome de conjunto de associações. (Obrigatória)  
  
- A associação de que irá conter instâncias. (Obrigatória)  
  
- Dois [conjuntos de associação terminam](association-set-end.md).  
  
## <a name="example"></a>Exemplo  

 O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy`, e `WrittenBy`. Embora informações sobre conjuntos de associações não é transmitida no diagrama, o diagrama a seguir mostra um exemplo de conjuntos de associações e conjuntos de entidades baseados nesse modelo.  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-set/example-model-three-entity-types.gif)  
  
 O exemplo a seguir mostra um conjunto de associações (`PublishedBy`) e dois conjuntos de entidades (`Books` e `Publishers`) com base no modelo conceitual mostrado acima. Bi no `Books` conjunto de entidades representa uma instância do `Book` tipo de entidade em tempo de execução. Da mesma forma, PJ representa uma `Publisher` instância no `Publishers` conjunto de entidades. BiPj representa uma instância da `PublishedBy` associação no conjunto de `PublishedBy` associação.  
  
 ![Captura de tela que mostra um exemplo de conjuntos.](./media/association-set/sets-example-association.gif)  
  
 O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais. CSDL seguir define um contêiner de entidade com um conjunto de associações para cada associação no diagrama anterior. Observe que o nome e a associação para cada conjunto de associações são definidos usando atributos XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 É possível definir vários conjuntos de associação por associação, desde que dois conjuntos de associação não compartilhem uma [extremidade de conjunto de associação](association-set-end.md). CSDL seguir define um contêiner de entidade com dois conjuntos de associações para associação de `WrittenBy` . Observe que os vários conjuntos de entidades foram definidos para os tipos de entidade de `Book` e de `Author` e que nenhum conjunto de associações compartilha fim do conjunto de associações.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Confira também

- [Conceitos chave do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
- [propriedade de chave estrangeira](foreign-key-property.md)
