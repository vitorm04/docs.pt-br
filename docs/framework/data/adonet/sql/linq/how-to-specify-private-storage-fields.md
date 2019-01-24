---
title: 'Como: Especificar campos de armazenamento particular'
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: d127de889fdaa2eb2d03a96dae5aa3d856efe32a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549580"
---
# <a name="how-to-specify-private-storage-fields"></a>Como: Especificar campos de armazenamento particular
Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> propriedade no <xref:System.Data.Linq.Mapping.DataAttribute> atributo para designar o nome de um campo de armazenamento subjacente.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a>Para especificar o nome de um armazenamento subjacente coloque  
  
1.  Adicione a propriedade de <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2.  Atribua o nome do campo como o valor da propriedade de <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> .  
  
## <a name="see-also"></a>Consulte também
- [O modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Como: Personalizar Classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
