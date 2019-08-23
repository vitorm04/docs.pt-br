---
title: 'Como: declarar colunas computadas'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 01c3442448285893ebb476ed11889e073065d4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943541"
---
# <a name="how-to-represent-computed-columns"></a>Como: declarar colunas computadas
Use a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> Propriedade em um <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para representar uma coluna cujo conteúdo é o resultado do cálculo.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não suporta colunas computadas como chaves primárias.  
  
### <a name="to-represent-a-computed-column"></a>Para representar uma coluna computado  
  
1. Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2. Atribuir uma representação de cadeia de caracteres de fórmula à propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> .  
  
## <a name="see-also"></a>Consulte também

- [O modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Como: Personalizar classes de entidade usando o editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
