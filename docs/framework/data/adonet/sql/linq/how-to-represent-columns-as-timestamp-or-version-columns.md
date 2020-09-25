---
title: 'Como: declarar colunas como colunas de carimbo de data/hora ou versão'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: cc8538ab7b2ecf5183cfb97995c04648493a369f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191743"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Como: declarar colunas como colunas de carimbo de data/hora ou versão

Use a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> Propriedade do <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar um campo ou propriedade como representando uma coluna de banco de dados que contém carimbos de data/hora do banco de dados ou números de versão.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>Para designar um campo ou propriedade como a representação de uma coluna de carimbo de data/hora ou a versão  
  
1. Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2. Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> a `true`.  
  
## <a name="see-also"></a>Veja também

- [Modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md)
- [Como: especificar quais membros são testados quanto a conflitos de simultaneidade](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [Como: personalizar classes de entidade usando o editor de códigos](how-to-customize-entity-classes-by-using-the-code-editor.md)
