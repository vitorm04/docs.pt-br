---
title: 'Como: Representar colunas como carimbo de hora ou colunas de versão'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: fa9ffe01c45df3ce0342b62e12007ddf88ee412d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674564"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Como: Representar colunas como carimbo de hora ou colunas de versão
Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> propriedade do <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar um campo ou propriedade como a representação de uma coluna de banco de dados que contém números de versão ou os carimbos de hora de banco de dados.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>Para designar um campo ou propriedade como a representação de uma coluna de carimbo de data/hora ou a versão  
  
1.  Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2.  Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> a `true`.  
  
## <a name="see-also"></a>Consulte também
- [O modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Como: Especificar que quais membros são testados para conflitos de simultaneidade](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [Como: Personalizar Classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
