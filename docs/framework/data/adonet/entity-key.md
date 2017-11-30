---
title: chave de entidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0d7df7ff1a0e8e732688e10befb4bffa86599d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-key"></a>chave de entidade
Um *chave da entidade* é um [propriedade](../../../../docs/framework/data/adonet/property.md) ou um conjunto de propriedades de um [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) que são usadas para determinar a identidade. As propriedades que compõem uma chave de entidade são escolhidas em tempo de design. Os valores das propriedades de chave de entidade devem identificar exclusivamente uma instância do tipo de entidade dentro de um [conjunto de entidades](../../../../docs/framework/data/adonet/entity-set.md) em tempo de execução. As propriedades que compõem uma chave de entidade devem ser escolhidas para garantir a exclusividade de instâncias em um conjunto de entidades.  
  
 A seguir estão os requisitos para um conjunto de propriedades ser uma chave de entidade:  
  
-   Nenhuma chave de duas entidades em um conjunto de entidades pode ser idêntica. Ou seja, para as duas entidades em um conjunto de entidades, os valores para todas as propriedades que constituem uma chave não podem ser os mesmos. No entanto, alguns (mas não todos os valores) que compõem uma chave de entidade podem ser os mesmos.  
  
-   Uma chave de entidade deve consistir em um conjunto de não anuláveis, imutável, [propriedades de tipo primitivo](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
-   As propriedades que compõem uma chave de entidade para um tipo de dado entidade não pode ser alterado. Você não pode permitir mais de uma chave possível de entidade para um tipo de dado; entidade as chaves substitutas não são suportadas.  
  
-   Quando uma entidade é empacotada em uma hierarquia de herança, a entidade raiz deve conter todas as propriedades que compõem a chave de entidade, e a chave de entidade deve ser definida no tipo de entidade raiz. Para obter mais informações, consulte [modelo de dados de entidade: herança](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`. As propriedades de cada tipo de entidade que compõem sua chave de entidade são denotadas com chave (“”). Observe que o tipo de entidade de `Author` tem uma chave de entidade que consiste em duas propriedades, `Name` e `Address`.  
  
 ![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL a seguir define o tipo de entidade de `Book` mostrado no diagrama anterior. Observe que a chave de entidade é definida pela propriedade de `ISBN` do tipo de objeto.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 A propriedade de `ISBN` é uma boa opção para a chave de entidade como um número de livro (ISBN) de padrão internacional identifica um livro.  
  
 CSDL a seguir define o tipo de entidade de `Author` mostrado no diagrama anterior. Observe que a chave de entidade consiste em duas propriedades, `Name` e `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Usar `Name` e `Address` para a chave de entidade é uma opção razoável, porque dois autores de mesmo nome é improvável de viver no mesmo endereço. No entanto, esta opção para uma chave de entidade não garante absolutamente chaves exclusivas de entidade em um conjunto de entidades. Adicione uma propriedade, como `AuthorId`, que pode ser usado para identificar exclusivamente um autor seria recomendado nesse caso.  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos chave do modelo de dados de entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de dados de entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
