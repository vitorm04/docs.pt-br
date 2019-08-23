---
title: 'Como: especificar quais membros são testados quanto a conflitos de simultaneidade'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: fc6fafa474805c2644bb2deabdceed192776ac76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938761"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Como: especificar quais membros são testados quanto a conflitos de simultaneidade
Aplique uma das três enums à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Propriedade em um <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para especificar quais membros devem ser incluídos nas verificações de atualização para a detecção de conflitos de simultaneidade otimista.  
  
 A propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (mapeada em tempo de design) é usada junto com recursos de simultaneidade de tempo de execução em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Para obter mais informações, [consulte simultaneidade otimista: Visão](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)geral.  
  
> [!NOTE]
> Os valores membro original são comparados com o estado atual de base de dados como nenhum membro é designado como `IsVersion=true`. Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Para usar sempre esse membro para detectar conflitos  
  
1. Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2. Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> a `Always`.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Para usar nunca esse membro para detectar conflitos  
  
1. Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2. Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> a `Never`.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Para usar este membro para detectar conflitos somente quando o aplicativo altere o valor do membro  
  
1. Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2. Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> a `WhenChanged`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir especifica que os objetos de `HomePage` nunca devem ser testados durante verificações de atualização. Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Gerenciar conflitos de alterações](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Realizando e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
