---
title: Sistema de tipo (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: f99d63bd526981c4a9f079c25851dc9bbd89cf7c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738467"
---
# <a name="type-system-entity-sql"></a>Sistema de tipo (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] dá suporte a vários tipos:  
  
- A primitiva) tipos simples (como `Int32` e `String.`  
  
- Tipos de substantivo que são definidos no esquema, como <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, e <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
- Tipos anônimos que não são definidos no esquema explicitamente: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, e <xref:System.Data.Metadata.Edm.RefType>.  
  
 Esta seção aborda os tipos anônimos que não estão definidos no esquema explicitamente, mas que têm suporte do Entity SQL. Para obter informações sobre os tipos primitivo e nominal, consulte [tipos de modelo conceitual (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).  
  
## <a name="rows"></a>Linhas  
 A estrutura de uma linha depende da sequência de membros tipados e nomeados em que a linha consiste. Um tipo de linha não tem nenhuma identidade e não pode ser herdada de. As instâncias do mesmo tipo de linha são equivalentes se os membros são equivalentes respectivamente. As linhas não têm nenhum comportamento além de sua equivalência estrutural e não têm equivalentes em Common Language Runtime. Consultas podem resultar em estruturas que contêm linhas ou coleções de linhas. API que associação entre as consultas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] e o idioma de host define como as linhas são feitas na consulta que gerou o resultado. Para obter informações sobre como construir uma instância de linha, consulte [construindo tipos](constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Coleções  
 Os tipos de coleção representam zero ou mais instâncias de outros objetos. Para obter informações sobre como construir a coleção, consulte [construindo tipos](constructing-types-entity-sql.md).  
  
## <a name="references"></a>Referências  
 Uma referência é um ponteiro a uma entidade lógica específica em um conjunto de entidades específico.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte aos seguintes operadores para construir, deconstruct, e navegar com referências:  
  
- [REF](ref-entity-sql.md)  
  
- [CREATEREF](createref-entity-sql.md)  
  
- [KEY](key-entity-sql.md)  
  
- [DEREF](deref-entity-sql.md)  
  
 Você pode navegar com uma referência usando o operador de acesso a membro (ponto) (`.`). O snippet a seguir na propriedade id (ordem) para navegar através da propriedade de r (referência).  
  
```sql  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Se o valor de referência é zero, ou se o destino de referência não existir, o resultado é nulo.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do Entity SQL](entity-sql-overview.md)
- [Referência de Entity SQL](entity-sql-reference.md)
- [CAST](cast-entity-sql.md)
- [CSDL, SSDL, and MSL Specifications](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) (Especificações CSDL, SSDL e MSL)
