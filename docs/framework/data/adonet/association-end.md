---
title: extremidade de associação
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 33cc2e10d9b72ef7f5f024905938c41fcc4a9755
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785052"
---
# <a name="association-end"></a>extremidade de associação
Uma *extremidade de associação* identifica o [tipo de entidade](entity-type.md) em uma extremidade de uma [Associação](association-type.md) e o número de instâncias de tipo de entidade que podem existir no final de uma associação. Termina de associação são definidas como parte de uma associação; uma associação deve ter exatamente duas termina de associação. [As propriedades de navegação](navigation-property.md) permitem a navegação de uma extremidade de associação para a outra.  
  
 Uma definição de fim de associação contém as informações a seguir:  
  
- Um dos tipos de entidade envolvidos na associação. (Necessário)  
  
    > [!NOTE]
    > Para uma associação determinada, o tipo de entidade especificada para cada o final da associação pode ser o mesmo. Isso cria uma dica associação.  
  
- Uma [multiplicidade de extremidade de associação](association-end-multiplicity.md) que indica o número de instâncias de tipo de entidade que podem estar em uma extremidade da associação. Uma multiplicidade de extremidade de associação pode ter um valor de um (1), zero ou um (0.. 1) ou muitos (\*).  
  
- Um nome para o final da associação. (Opcional)  
  
- Informações sobre as operações que são executadas no final da associação, como em cascata exclusão. (Opcional)  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy` e `WrittenBy`. Terminar a associação para associação de `PublishedBy` são os tipos de entidade de `Book` e de `Publisher` . A multiplicidade do `Publisher` final é um (1) e a multiplicidade `Book` do final é Many (\*), indicando que um Publicador publica muitos livros e um livro é publicado por um Publicador.  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-end/example-model-three-entity-types.gif)  
  
 O Entity Framework ADO.NET usa uma DSL (linguagem específica de domínio) chamada[CSDL](./ef/language-reference/csdl-specification.md)(linguagem de definição de esquema conceitual) para definir modelos conceituais. CSDL a seguir define a associação de `PublishedBy` mostrada no diagrama anterior. Observe que o tipo, nome, e a multiplicidade de cada o final da associação são especificados por atributos XML ( `Type`, `Role`, e atributos de `Multiplicity` , respectivamente). Opcional informações sobre as operações executadas em uma extremidade é especificado em um elemento XML (o elemento de `OnDelete` ). Nesse caso, se um editor é excluído, é para todos livros associados.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
