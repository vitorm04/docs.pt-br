---
title: 'Como: declarar colunas com permissão de valores nulos'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 00a837467010c2d8a9f0ca16d6aba2fc5f4c973f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781814"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a>Como: declarar colunas com permissão de valores nulos
Use a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> propriedade no<xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para especificar que a coluna de banco de dados associada pode conter valores nulos.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a>Para designar uma coluna como permitir valores nulos  
  
1. Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2. Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> a `true`.  
  
## <a name="see-also"></a>Consulte também

- [O modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md)
- [Como: Personalizar classes de entidade usando o editor de código](how-to-customize-entity-classes-by-using-the-code-editor.md)
