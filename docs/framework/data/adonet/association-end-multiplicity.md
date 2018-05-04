---
title: multiplicidade da extremidade da associação
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 2f70fa4b163b957ea1e43506033863c3540b0418
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="association-end-multiplicity"></a>multiplicidade da extremidade da associação
*Multiplicidade da extremidade da associação* define o número de [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) instâncias que podem ser de uma extremidade de um [associação](../../../../docs/framework/data/adonet/association-type.md).  
  
 Uma multiplicidade do final da associação pode ter um dos seguintes valores:  
  
-   um (1): Indica que exatamente uma instância do tipo de entidade existe no final da associação.  
  
-   zero ou um 0..1 (:) Indica que essa instâncias de zero ou mais tipos de entidade existem no final da associação.  
  
-   muitos (*): Indica que zero, uma, ou mais instâncias do tipo de entidade existem no final da associação.  
  
 Uma associação é caracterizada frequentemente pelos multiplicities final da associação. Por exemplo, se as extremidades de uma associação têm um multiplicities (1) e muitos (*), a associação é chamada de um para muitos associação. No exemplo abaixo, a associação de `PublishedBy` é um para muitos associação (um editor publica muitos livros e um livro é publicado por um editor). A associação de `WrittenBy` é um muitos para muitos associação (um livro pode ter vários autores e um autor pode escrever diversos livros).  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy` e `WrittenBy`. Terminar a associação para associação de `PublishedBy` são os tipos de entidade de `Book` e de `Publisher` . A multiplicidade do final de `Publisher` é um (1) e a multiplicidade do final de `Book` é muitas (*).  
  
 ![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 O ADO.NET Entity Framework usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define a associação de `PublishedBy` mostrada no diagrama anterior:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Consulte também  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
