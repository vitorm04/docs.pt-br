---
title: multiplicidade da extremidade da associação
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 59eed56204543adf405cfc7c71a49697a9e18374
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135025"
---
# <a name="association-end-multiplicity"></a>multiplicidade da extremidade da associação
*Multiplicidade de extremidades de associação* define o número de [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) instâncias que podem estar em uma extremidade de uma [associação](../../../../docs/framework/data/adonet/association-type.md).  
  
 Uma multiplicidade do final da associação pode ter um dos seguintes valores:  
  
-   um (1): Indica se que essa instância de tipo exatamente uma entidade existe no final da associação.  
  
-   zero ou um (entre 0 e 1): Indica que zero ou uma instância de tipo de entidade existe no final da associação.  
  
-   muitos (\*): indica que zero, um ou mais instâncias de tipo de entidade existem no final da associação.  
  
 Uma associação é caracterizada frequentemente pelos multiplicities final da associação. Por exemplo, se as extremidades de uma associação tem multiplicidades um (1) e muitos (\*), a associação é chamada de uma associação um-para-muitos. No exemplo abaixo, a associação de `PublishedBy` é um para muitos associação (um editor publica muitos livros e um livro é publicado por um editor). A associação de `WrittenBy` é um muitos para muitos associação (um livro pode ter vários autores e um autor pode escrever diversos livros).  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy` e `WrittenBy`. Terminar a associação para associação de `PublishedBy` são os tipos de entidade de `Book` e de `Publisher` . A multiplicidade do `Publisher` final é um (1) e a multiplicidade do `Book` end é muitas (\*).  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 O ADO.NET Entity Framework usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define a associação de `PublishedBy` mostrada no diagrama anterior:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
