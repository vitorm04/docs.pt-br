---
title: tipo de entidade
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: c694f29d36988ea52aeca650cf2bba2c50c91e89
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765315"
---
# <a name="entity-type"></a>tipo de entidade
O *tipo de entidade* é o bloco de construção fundamental para descrever a estrutura de dados com modelo de dados de entidade (EDM). Em um modelo conceitual, um tipo de entidade representa a estrutura dos conceitos de nível superior, como clientes ou pedidos. Um tipo de entidade é um modelo para instâncias do tipo de objeto. Cada modelo contém as informações a seguir:  
  
-   Um nome exclusivo. (Obrigatório.)  
  
-   Um [chave da entidade](../../../../docs/framework/data/adonet/entity-key.md) definido por uma ou mais propriedades. (Obrigatório.)  
  
-   Os dados na forma de [propriedades](../../../../docs/framework/data/adonet/property.md). (Opcional).  
  
-   [Propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) que permitem de navegação de um [final](../../../../docs/framework/data/adonet/association-end.md) de um [associação](../../../../docs/framework/data/adonet/association-type.md) para a outra. (Opcional)  
  
 Em um aplicativo, uma instância de um tipo de entidade representa um objeto específico (como um cliente ou uma ordem específica.) Cada instância de um tipo de entidade deve ter uma única [chave da entidade](../../../../docs/framework/data/adonet/entity-key.md) dentro de um [conjunto de entidades](../../../../docs/framework/data/adonet/entity-set.md).  
  
 Duas instâncias do tipo de entidade são consideradas iguais somente se são do mesmo tipo e os valores das chaves de entidade são os mesmos.  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`:  
  
 ![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Observe que as propriedades de cada tipo de entidade que compõem sua chave de entidade são denotadas com chave (“”).  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define o tipo de entidade de `Book` mostrado no diagrama anterior:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Consulte também  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [facet](../../../../docs/framework/data/adonet/facet.md)
