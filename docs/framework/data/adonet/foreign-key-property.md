---
title: propriedade de chave estrangeira
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 8680019f6f1a53233b5c49163f474cf33409b69b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674465"
---
# <a name="foreign-key-property"></a>propriedade de chave estrangeira
Um *propriedade de chave estrangeira* no modelo de dados de entidade (EDM) é um tipo primitivo [propriedade](../../../../docs/framework/data/adonet/property.md) (ou um conjunto de propriedades de tipo primitivo) em um [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) que contém a [chave de entidade](../../../../docs/framework/data/adonet/entity-key.md) de outro tipo de entidade.  
  
 Uma propriedade de chave externa é análogo a uma coluna de chave externa em uma base de dados relacional. Da mesma forma que colunas de chave estrangeira são usadas em um banco de dados relacional para criar relações entre linhas em tabelas, as propriedades de chave estrangeira em um modelo conceitual são usadas para estabelecer [associações](../../../../docs/framework/data/adonet/association-type.md) entre tipos de entidade. Um [restrição de integridade referencial](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) é usado para definir uma associação entre dois tipos de entidade quando um dos tipos tem uma propriedade de chave estrangeira.  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`. O tipo de entidade de `Book` tem uma propriedade, `PublisherId`, que faz referência a chave de entidade do tipo de entidade de `Publisher` quando você define uma restrição de integridade referencial em associação de `PublishedBy` .  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "exemplo de um modelo de restrição referencial")  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir usa a propriedade `PublisherId` de chave externa para definir uma restrição de integridade referencial em associação de `PublishedBy` mostrada no modelo conceitual mostrado acima.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Consulte também
- [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
