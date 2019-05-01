---
title: 'Como: especificar quando exceções de simultaneidade são geradas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 30dd83c68472ecd3244cfc87b6df97b948b9a84f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033625"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Como: especificar quando exceções de simultaneidade são geradas
Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], uma exceção é lançada de <xref:System.Data.Linq.ChangeConflictException> quando os objetos não atualizarão devido a conflitos de concorrência otimista. Para obter mais informações, consulte [a simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Antes de enviar as alterações para base de dados, você pode especificar quando exceções concorrentes devem ser lançadas:  
  
- Lance a exceção na primeira falha (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
- Concluir todas as tentativas de atualização, se acumule quaisquer falhas, e relatar falhas criadas na exceção (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Quando lançada, a exceção de <xref:System.Data.Linq.ChangeConflictException> fornece acesso a uma coleção de <xref:System.Data.Linq.ChangeConflictCollection> . Essa coleção fornece detalhes para cada conflito (mapeado para uma tentativa única falha de atualização), incluindo o acesso à coleção de <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> . Mapas de cada conflito de membro a um único membro na atualização que falhou a verificação de simultaneidade.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra exemplos de ambos os valores.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Realizando e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
