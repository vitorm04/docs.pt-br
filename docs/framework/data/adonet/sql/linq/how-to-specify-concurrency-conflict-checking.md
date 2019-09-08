---
title: 'Como: especificar a verificação de conflito de simultaneidade'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: fd3db5eb5dc9b74d8ea33af56dd522cf2f3fecdb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781592"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a>Como: especificar a verificação de conflito de simultaneidade
Você pode especificar quais colunas de base de dados devem ser marcadas para ver se houver conflitos de simultaneidade quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Para obter mais informações, confira [Como: Especifique quais membros são testados para conflitos](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)de simultaneidade.  
  
## <a name="example"></a>Exemplo  
 O código a seguir especifica que o membro de `HomePage` nunca deve ser testado durante verificações de atualização. Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [O modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md)
- [Como: Personalizar classes de entidade usando o editor de código](how-to-customize-entity-classes-by-using-the-code-editor.md)
