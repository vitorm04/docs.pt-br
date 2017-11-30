---
title: "Como: Especificar quais membros são testados para conflitos de simultaneidade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6c13c5d6578f27155b87744ed8730f5fae2e1e25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Como: Especificar quais membros são testados para conflitos de simultaneidade
Aplicar um dos três enums para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> propriedade em um <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para especificar quais membros devem ser incluídos na atualização verifica a detecção de conflitos de simultaneidade otimista.  
  
 A propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (mapeada em tempo de design) é usada junto com recursos de simultaneidade de tempo de execução em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Para obter mais informações, consulte [simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Os valores membro original são comparados com o estado atual de base de dados como nenhum membro é designado como `IsVersion=true`. Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Para usar sempre esse membro para detectar conflitos  
  
1.  Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2.  Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> a `Always`.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Para usar nunca esse membro para detectar conflitos  
  
1.  Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2.  Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> a `Never`.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Para usar este membro para detectar conflitos somente quando o aplicativo altere o valor do membro  
  
1.  Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2.  Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> a `WhenChanged`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir especifica que os objetos de `HomePage` nunca devem ser testados durante verificações de atualização. Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Fazendo e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
