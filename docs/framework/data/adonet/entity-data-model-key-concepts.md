---
title: Conceitos chave do Modelo de Dados de Entidade
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: bcfc9cbb82a23dcb4d33ca8a838a49eac7180111
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825658"
---
# <a name="entity-data-model-key-concepts"></a>Conceitos chave do Modelo de Dados de Entidade
Modelo de dados de entidade (EDM) usa três conceitos principais para descrever a estrutura de dados: *tipo de entidade*, *tipo de associação*, e *propriedade*. Esses são os conceitos mais importantes para descrever a estrutura dos dados em qualquer implementação do EDM.  
  
## <a name="entity-type"></a>Tipo de entidade  
 O [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) é o bloco de construção fundamental para descrever a estrutura de dados com o modelo de dados de entidade. Em um modelo conceitual, tipos de entidade são construídos a partir [propriedades](../../../../docs/framework/data/adonet/property.md) e descrever a estrutura dos conceitos de nível superior, como clientes e pedidos em um aplicativo de negócios. Da mesma forma que uma definição de classe em um programa de computador é um modelo para instâncias da classe, um tipo de entidade é um modelo para entidades. Uma entidade representa um objeto específico (como um cliente ou um pedido específico.) Cada entidade deve ter um único [chave de entidade](../../../../docs/framework/data/adonet/entity-key.md) dentro de uma [conjunto de entidades](../../../../docs/framework/data/adonet/entity-set.md).  Um conjunto de entidades é uma coleção de instâncias de um tipo de entidade específico. Conjuntos de entidades (e [conjuntos de associações](../../../../docs/framework/data/adonet/association-set.md)) são agrupados logicamente em um [contêiner de entidade](../../../../docs/framework/data/adonet/entity-container.md).  
  
 A herança é suportada com tipos de entidade: isto é, um tipo de entidade pode ser derivado de outro. Para obter mais informações, consulte [modelo de dados de entidade: Herança](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>Tipo de associação  
 Uma [tipo de associação](../../../../docs/framework/data/adonet/association-type.md) (também chamado de uma associação) é o bloco de construção fundamental para descrever relações no modelo de dados de entidade. Em um modelo conceitual, uma associação representa uma relação entre dois tipos de entidade (como cliente e pedido). Cada associação possui duas [extremidades de associação](../../../../docs/framework/data/adonet/association-end.md) que especificam os tipos de entidade envolvidos na associação. Cada extremidade da associação também especifica um [multiplicidade do final da associação](../../../../docs/framework/data/adonet/association-end-multiplicity.md) que indica o número de entidades que podem estar nessa extremidade da associação. Uma multiplicidade de extremidades de associação pode ter um valor igual a um (1), a zero ou a um (0..1) ou a muitos (*). Entidades em uma extremidade de uma associação podem ser acessadas por meio [propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md), ou por meio de chaves estrangeiras se são expostos em um tipo de entidade. Para obter mais informações, consulte [propriedade de chave estrangeira](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
 Em um aplicativo, uma instância de uma associação representa uma associação específica (como uma associação entre uma instância de cliente e instâncias de pedido). Instâncias de associação são agrupadas logicamente em um [conjunto de associações](../../../../docs/framework/data/adonet/association-set.md). Conjuntos de associações (e [conjuntos de entidades](../../../../docs/framework/data/adonet/entity-set.md)) são agrupados logicamente em um [contêiner de entidade](../../../../docs/framework/data/adonet/entity-container.md).  
  
## <a name="property"></a>Propriedade  
 [Tipos de entidade](../../../../docs/framework/data/adonet/entity-type.md) conter [propriedades](../../../../docs/framework/data/adonet/property.md) que definem sua estrutura e características. Por exemplo, um tipo de entidade de cliente pode ter propriedades como CustomerId, Name e Address.  
  
 As propriedades em um modelo conceitual são análogas às propriedades definidas em uma classe em um programa de computador. Da mesma forma que as propriedades em uma classe definem a forma da classe e transportam informações sobre objetos, as propriedades em um modelo conceitual definem a forma de um tipo de entidade e transportam informações sobre as instâncias dos tipos de entidade.  
  
 Uma propriedade pode conter dados primitivos (como uma cadeia de caracteres, um número inteiro ou um valor booliano) ou dados estruturados (como um tipo complexo). Para obter mais informações, consulte [modelo de dados de entidade: Tipos de dados primitivos](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Representações de um modelo conceitual  
 Um *modelo conceitual* é uma representação específica da estrutura de alguns dados como entidades e relações. Uma maneira de representar um modelo conceitual é com um diagrama. O diagrama a seguir representa um modelo conceitual com três tipos de entidade (`Book`, `Publisher` e `Author`) e duas associações (`PublishedBy` e `WrittenBy`):  
  
 ![Diagrama que mostra um modelo conceitual com três tipos de entidade.](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 Essa representação, no entanto, tem alguns defeitos quando se trata de transmitir alguns detalhes sobre o modelo. Por exemplo, o tipo de propriedade e as informações do conjunto de entidades não são transportados no diagrama. A sofisticação de um modelo conceitual pode ser transmitida mais claramente com um DSL (linguagem específica do domínio). O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma DSL baseado em XML chamada *linguagem de definição de esquema conceitual* ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. O seguinte é a definição CSDL do modelo conceitual no diagrama anterior:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Consulte também
- [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
