---
title: multiplicidade da extremidade da associação
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 3f3d8ba9f7e68065024dd3efb599b847496740cd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738572"
---
# <a name="association-end-multiplicity"></a>multiplicidade da extremidade da associação
A *multiplicidade de extremidade de associação* define o número de instâncias de tipo de [entidade](entity-type.md) que podem estar em uma extremidade de uma [Associação](association-type.md).  
  
 Uma multiplicidade do final da associação pode ter um dos seguintes valores:  
  
- um (1): Indica que exatamente uma instância do tipo de entidade existe no final da associação.  
  
- zero ou um 0..1 (:) Indica que essa instâncias de zero ou mais tipos de entidade existem no final da associação.  
  
- muitos (\*): indica que zero, uma ou mais instâncias de tipo de entidade existem na extremidade da associação.  
  
 Uma associação é caracterizada frequentemente pelos multiplicities final da associação. Por exemplo, se as extremidades de uma associação tiverem multiplicidade um (1) e muitos (\*), a associação será chamada de associação um-para-muitos. No exemplo abaixo, a associação de `PublishedBy` é um para muitos associação (um editor publica muitos livros e um livro é publicado por um editor). A associação de `WrittenBy` é um muitos para muitos associação (um livro pode ter vários autores e um autor pode escrever diversos livros).  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy` e `WrittenBy`. Terminar a associação para associação de `PublishedBy` são os tipos de entidade de `Book` e de `Publisher` . A multiplicidade do `Publisher` end é um (1) e a multiplicidade do `Book` end é Many (\*).  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 O Entity Framework ADO.NET usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais. CSDL seguir define a associação de `PublishedBy` mostrada no diagrama anterior:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
