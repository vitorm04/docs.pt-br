---
title: "propriedade de navegação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f5af52532dc534d793e7e8ce72a08c2f7229569b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="navigation-property"></a>propriedade de navegação
Um *propriedade de navegação* é uma propriedade opcional em uma [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) que permite a navegação de um [final](../../../../docs/framework/data/adonet/association-end.md) de um [associação](../../../../docs/framework/data/adonet/association-type.md) para a outra extremidade. Ao contrário de outras [propriedades](../../../../docs/framework/data/adonet/property.md), propriedades de navegação não contêm dados.  
  
 Uma definição de propriedade de navegação inclui o seguinte:  
  
-   Um nome. (Necessário)  
  
-   A associação que navega. (Necessário)  
  
-   Termina de associação que navega. (Necessário)  
  
 Observe que as propriedades de navegação são opcionais em ambos os tipos de entidade termina de uma associação. Se você definir uma propriedade de navegação em um tipo de entidade no final de uma associação, você não precisa definir uma propriedade de navegação no tipo de entidade no outro extremo de associação.  
  
 O tipo de dados de uma propriedade de navegação é determinado pelo [multiplicidade](../../../../docs/framework/data/adonet/association-end-multiplicity.md) do seu remote [end de associação](../../../../docs/framework/data/adonet/association-end.md). Por exemplo, suponha uma propriedade de navegação, `OrdersNavProp`, existe em um tipo de entidade de `Customer` e navegar em um para muitos associação entre `Customer` e `Order`. Porque o fim remoto da associação para a propriedade de navegação tem a multiplicidade de muitos (*), seu tipo de dados é uma coleção (de `Order`). Da mesma forma, se uma propriedade de navegação, `CustomerNavProp`, existe no tipo de entidade de `Order` , seu tipo de dados deve ser `Customer`, porque a multiplicidade de extremidade remoto é um (1).  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`. As propriedades de navegação, `Publisher` e `Authors`, são definidas no tipo de entidade de livro. A propriedade `Books` de navegação é definida no tipo de entidade do Publisher e tipo de entidade de `Author` .  
  
 ![Modelo com propriedades de navegação](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define o tipo de entidade de `Book` mostrado no diagrama anterior:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Observe que os atributos XML são usados para comunicar informações necessárias para definir uma propriedade de navegação: O atributo `Name` contém o nome da propriedade, `Relationship` contém o nome da associação que navega, e `FromRole` e `ToRole` contêm terminar a associação.  
  
## <a name="see-also"></a>Consulte também  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
