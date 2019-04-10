---
title: 'Como: especificar tipos de dados de banco de dados'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: bf53463be8c715fd1c599efac1b19d838be19f86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218037"
---
# <a name="how-to-specify-database-data-types"></a>Como: especificar tipos de dados de banco de dados
Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> propriedade em um <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para especificar o texto exato que define a coluna em uma declaração de tabela T-SQL.  
  
 Você deve especificar a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> somente se você planejar usar <xref:System.Data.Linq.DataContext.CreateDatabase%2A> para criar uma instância de base de dados.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Para especificar o texto para definir um tipo de dados em uma tabela T-SQL  
  
1.  Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2.  Defina o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> ao texto exato que é usado por T-SQL.  
  
## <a name="see-also"></a>Consulte também

- [Modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Como: personalizar classes de entidade usando o editor de códigos](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
