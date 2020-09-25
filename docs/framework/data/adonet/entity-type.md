---
title: tipo de entidade
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 3f99667a06d8aa439232802d4909290dfe9db97c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194772"
---
# <a name="entity-type"></a>tipo de entidade

O *tipo de entidade* é o bloco de construção fundamental para descrever a estrutura de dados com o modelo de dados de entidade (EDM). Em um modelo conceitual, um tipo de entidade representa a estrutura dos conceitos de nível superior, como clientes ou pedidos. Um tipo de entidade é um modelo para instâncias do tipo de objeto. Cada modelo contém as informações a seguir:  
  
- Um nome exclusivo. (Obrigatório.)  
  
- Uma [chave de entidade](entity-key.md) definida por uma ou mais propriedades. (Obrigatório.)  
  
- Dados na forma de [Propriedades](property.md). (Opcional).  
  
- [Propriedades de navegação](navigation-property.md) que permitem a navegação de uma [extremidade](association-end.md) de uma [Associação](association-type.md) para a outra extremidade. (Opcional)  
  
 Em um aplicativo, uma instância de um tipo de entidade representa um objeto específico (como um cliente ou uma ordem específica.) Cada instância de um tipo de entidade deve ter uma [chave de entidade](entity-key.md) exclusiva dentro de um [conjunto de entidades](entity-set.md).  
  
 Duas instâncias do tipo de entidade são consideradas iguais somente se são do mesmo tipo e os valores das chaves de entidade são os mesmos.  
  
## <a name="example"></a>Exemplo  

 O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`:  
  
 ![Modelo de exemplo com três tipos de entidade](./media/entity-type/example-model-three-entity-types.gif)  
  
 Observe que as propriedades de cada tipo de entidade que compõem sua chave de entidade são denotadas com chave (“”).  
  
 O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais. CSDL seguir define o tipo de entidade de `Book` mostrado no diagrama anterior:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Veja também

- [Conceitos chave do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
- [particular](facet.md)
