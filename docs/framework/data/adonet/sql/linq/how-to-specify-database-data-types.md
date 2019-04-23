---
title: 'Como: especificar tipos de dados de banco de dados'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 67f23ff06aefbcff4ba7e2eaab63d9b8493b9717
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333204"
---
# <a name="how-to-specify-database-data-types"></a>Como: especificar tipos de dados de banco de dados
Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> propriedade em um <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para especificar o texto exato que define a coluna em uma declaração de tabela T-SQL.  
  
 Você deve especificar a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> somente se você planejar usar <xref:System.Data.Linq.DataContext.CreateDatabase%2A> para criar uma instância de base de dados.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Para especificar o texto para definir um tipo de dados em uma tabela T-SQL  
  
1. Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2. Defina o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> ao texto exato que é usado por T-SQL.  
  
## <a name="see-also"></a>Consulte também

- [O modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Como: Personalizar Classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
