---
title: 'Como: especificar campos de armazenamento particular'
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: 843b7ae8dbddb76e0e5fa33d3594a5655dbf1a37
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302446"
---
# <a name="how-to-specify-private-storage-fields"></a>Como: especificar campos de armazenamento particular
Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> propriedade no <xref:System.Data.Linq.Mapping.DataAttribute> atributo para designar o nome de um campo de armazenamento subjacente.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a>Para especificar o nome de um armazenamento subjacente coloque  
  
1. Adicione a propriedade de <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2. Atribua o nome do campo como o valor da propriedade de <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> .  
  
## <a name="see-also"></a>Consulte também

- [Modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Como: personalizar classes de entidade usando o editor de códigos](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
