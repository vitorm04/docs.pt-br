---
title: extremidade de associação
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 575157cd1d125d3315e1859aad72cc8b08d8b4cf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932209"
---
# <a name="association-end"></a>extremidade de associação
Uma *extremidade de associação* identifica o [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) em uma extremidade de uma [Associação](../../../../docs/framework/data/adonet/association-type.md) e o número de instâncias de tipo de entidade que podem existir no final de uma associação. Termina de associação são definidas como parte de uma associação; uma associação deve ter exatamente duas termina de associação. [As propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) permitem a navegação de uma extremidade de associação para a outra.  
  
 Uma definição de fim de associação contém as informações a seguir:  
  
- Um dos tipos de entidade envolvidos na associação. (Necessário)  
  
    > [!NOTE]
    > Para uma associação determinada, o tipo de entidade especificada para cada o final da associação pode ser o mesmo. Isso cria uma dica associação.  
  
- Uma [multiplicidade de extremidade de associação](../../../../docs/framework/data/adonet/association-end-multiplicity.md) que indica o número de instâncias de tipo de entidade que podem estar em uma extremidade da associação. Uma multiplicidade de extremidade de associação pode ter um valor de um (1), zero ou um (0.. 1) ou muitos (\*).  
  
- Um nome para o final da associação. (Opcional)  
  
- Informações sobre as operações que são executadas no final da associação, como em cascata exclusão. (Opcional)  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy` e `WrittenBy`. Terminar a associação para associação de `PublishedBy` são os tipos de entidade de `Book` e de `Publisher` . A multiplicidade do `Publisher` final é um (1) e a multiplicidade `Book` do final é Many (\*), indicando que um Publicador publica muitos livros e um livro é publicado por um Publicador.  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-end/example-model-three-entity-types.gif)  
  
 O Entity Framework ADO.NET usa uma DSL (linguagem específica de domínio) chamada[CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)(linguagem de definição de esquema conceitual) para definir modelos conceituais. CSDL a seguir define a associação de `PublishedBy` mostrada no diagrama anterior. Observe que o tipo, nome, e a multiplicidade de cada o final da associação são especificados por atributos XML ( `Type`, `Role`, e atributos de `Multiplicity` , respectivamente). Opcional informações sobre as operações executadas em uma extremidade é especificado em um elemento XML (o elemento de `OnDelete` ). Nesse caso, se um editor é excluído, é para todos livros associados.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
