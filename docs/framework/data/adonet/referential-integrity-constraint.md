---
title: restrição de integridade referencial
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: b442e15c75554e1b06e9ff89c7224430a0605f9c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649634"
---
# <a name="referential-integrity-constraint"></a>restrição de integridade referencial
Um *restrição de integridade referencial* no modelo de dados de entidade (EDM) é semelhante a uma restrição de integridade referencial em um banco de dados relacional. Da mesma forma que uma coluna (ou colunas) de uma tabela de banco de dados podem fazer referência a chave primária de outra tabela, uma [propriedade](../../../../docs/framework/data/adonet/property.md) (ou propriedades) de um [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) pode fazer referência a [chave de entidade ](../../../../docs/framework/data/adonet/entity-key.md) de outro tipo de entidade. O tipo de entidade que é referenciado é chamado de *final principal* da restrição. O tipo de entidade que faz referência a extremidade de entidade é chamado de *final dependente* da restrição.  
  
 Uma restrição de integridade referencial é definida como parte de um [associação](../../../../docs/framework/data/adonet/association-type.md) entre dois tipos de entidade. A definição de uma restrição de integridade referencial especifica as seguintes informações:  
  
- O final principal de restrição. (Um tipo de entidade cuja chave de entidade é referenciada pela o final dependente.)  
  
- A chave de entidade de extremidade principal.  
  
- O final dependente de restrição. (Um tipo de entidade que tem uma propriedade ou um propriedades que referenciem a chave de entidade de extremidade principal.)  
  
- A propriedade ou propriedades referência de extremidade dependente.  
  
 O objetivo de restrições de integridade referencial em EDM é garantir que as associações válidos sempre existe. Para obter mais informações, consulte [propriedade de chave estrangeira](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com duas associações: `WrittenBy` e `PublishedBy`. O tipo de entidade de `Book` tem uma propriedade, `PublisherId`, que faz referência a chave de entidade do tipo de entidade de `Publisher` quando você define uma restrição de integridade referencial em associação de `PublishedBy` .  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "exemplo de um modelo de restrição referencial")  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define uma restrição de integridade referencial em associação de `PublishedBy` mostrada no modelo conceitual anterior.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
