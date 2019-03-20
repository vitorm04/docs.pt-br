---
title: extremidade de associação
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: c1b43dea98b65427065387aedd2305f9c7b370bd
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185578"
---
# <a name="association-end"></a>extremidade de associação
Uma *final da associação* identifica as [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) em uma extremidade de um [associação](../../../../docs/framework/data/adonet/association-type.md) e o número de entidade instâncias que podem existir na fim de uma associação de tipo. Termina de associação são definidas como parte de uma associação; uma associação deve ter exatamente duas termina de associação. [Propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) permite a navegação de uma extremidade de associação para o outro.  
  
 Uma definição de fim de associação contém as informações a seguir:  
  
-   Um dos tipos de entidade envolvidos na associação. (Necessário)  
  
    > [!NOTE]
    >  Para uma associação determinada, o tipo de entidade especificada para cada o final da associação pode ser o mesmo. Isso cria uma dica associação.  
  
-   Uma [multiplicidade do final da associação](../../../../docs/framework/data/adonet/association-end-multiplicity.md) que indica o número de instâncias do tipo de entidade que pode estar em uma extremidade da associação. Uma multiplicidade de extremidades de associação pode ter um valor de um (1), zero ou um (entre 0 e 1) ou muitas (\*).  
  
-   Um nome para o final da associação. (Opcional)  
  
-   Informações sobre as operações que são executadas no final da associação, como em cascata exclusão. (Opcional)  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy` e `WrittenBy`. Terminar a associação para associação de `PublishedBy` são os tipos de entidade de `Book` e de `Publisher` . A multiplicidade do `Publisher` final é um (1) e a multiplicidade do `Book` end é muitas (\*), indicando que um editor publica muitos livros e um livro é publicado por um editor.  
  
 ![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 O ADO.NET Entity Framework usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL a seguir define a associação de `PublishedBy` mostrada no diagrama anterior. Observe que o tipo, nome, e a multiplicidade de cada o final da associação são especificados por atributos XML ( `Type`, `Role`, e atributos de `Multiplicity` , respectivamente). Opcional informações sobre as operações executadas em uma extremidade é especificado em um elemento XML (o elemento de `OnDelete` ). Nesse caso, se um editor é excluído, é para todos livros associados.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Consulte também
- [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
