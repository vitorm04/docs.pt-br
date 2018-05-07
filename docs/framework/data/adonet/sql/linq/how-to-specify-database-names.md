---
title: 'Como: Especificar nomes de base de dados'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a69fa1723c0660d3c6dfa8bfa7ec3b9e4dc75d7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-database-names"></a>Como: Especificar nomes de base de dados
Use a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> em um atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para especificar o nome de uma base de dados quando um nome não é fornecido pela conexão.  
  
 Para exemplos de códigos, consulte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### <a name="to-specify-the-name-of-the-database"></a>Para especificar o nome de base de dados  
  
1.  Adicione o atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> para a declaração de classe para o base de dados.  
  
2.  Adicione a propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> ao atributo de <xref:System.Data.Linq.Mapping.DatabaseAttribute> .  
  
3.  Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> o nome que você deseja especificar.  
  
## <a name="see-also"></a>Consulte também  
 [O modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Como personalizar classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
