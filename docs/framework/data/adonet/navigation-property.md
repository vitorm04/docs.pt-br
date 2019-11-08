---
title: Propriedade de navegação-ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: afb2043abf70fa92ea7cdf8d1e8246d5cdfdba74
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738392"
---
# <a name="navigation-property"></a>Propriedade de navegação

Uma *propriedade de navegação* é uma propriedade opcional em [um tipo de entidade](entity-type.md) que permite a navegação de uma [extremidade](association-end.md) de uma [Associação](association-type.md) para a outra extremidade. Ao contrário de outras [Propriedades](property.md), as propriedades de navegação não contêm dados.

Uma definição de propriedade de navegação inclui o seguinte:

- Um nome. (Necessário)

- A associação que navega. (Necessário)

- Termina de associação que navega. (Necessário)

Observe que as propriedades de navegação são opcionais em ambos os tipos de entidade termina de uma associação. Se você definir uma propriedade de navegação em um tipo de entidade no final de uma associação, você não precisa definir uma propriedade de navegação no tipo de entidade no outro extremo de associação.

O tipo de dados de uma propriedade de navegação é determinado pela [multiplicidade](association-end-multiplicity.md) de sua [extremidade de associação](association-end.md)remota. Por exemplo, suponha uma propriedade de navegação, `OrdersNavProp`, existe em um tipo de entidade de `Customer` e navegar em um para muitos associação entre `Customer` e `Order`. Como a extremidade de associação remota para a propriedade de navegação tem multiplicidade de muitos (\*), seu tipo de dados é uma coleção (de `Order`). Da mesma forma, se uma propriedade de navegação, `CustomerNavProp`, existe no tipo de entidade de `Order` , seu tipo de dados deve ser `Customer`, porque a multiplicidade de extremidade remoto é um (1).

## <a name="example"></a>Exemplo

O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`. As propriedades de navegação, `Publisher` e `Authors`, são definidas no tipo de entidade de livro. A propriedade `Books` de navegação é definida no tipo de entidade do Publisher e tipo de entidade de `Author` .

 ![Diagrama mostrando um modelo conceitual com três tipos de entidade.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais. CSDL seguir define o tipo de entidade de `Book` mostrado no diagrama anterior:

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

Observe que os atributos XML são usados para comunicar informações necessárias para definir uma propriedade de navegação: O atributo `Name` contém o nome da propriedade, `Relationship` contém o nome da associação que navega, e `FromRole` e `ToRole` contêm terminar a associação.

## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
- [Relações, propriedades de navegação e chaves estrangeiras](/ef/ef6/fundamentals/relationships)
