---
title: 'Como: resolver conflitos substituindo valores de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 1da2abcbbb3b87d44aa99016112d9ef2674912c6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781722"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Como: resolver conflitos substituindo valores de banco de dados
Para reconciliar diferenças entre valores esperados e reais de base de dados antes que você submeter tente novamente suas alterações, você pode usar <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> para substituir valores de base de dados. Para obter mais informações, [consulte simultaneidade otimista: Visão](optimistic-concurrency-overview.md)geral.  
  
> [!NOTE]
> Em todos os casos, o registro no cliente é atualizado primeiro recuperando os dados atualizados de base de dados. Esta ação certifique-se de que a seguir tentativa de atualização não falhará nas mesmas verificação de simultaneidade.  
  
## <a name="example"></a>Exemplo  
 Nesse cenário, uma exceção é lançada de <xref:System.Data.Linq.ChangeConflictException> quando tenta User1 para enviar alterações, porque Usuário2 tiver alterado entretanto as colunas do assistente e departamento. A tabela a seguir mostra a situação.  
  
||Manager|Assistente|Departamento|  
|------|-------------|---------------|----------------|  
|Estado original de base de dados quando consultado por User1 e por Usuário2.|Alfreds|Maria|Vendas|  
|User1 prepara-se para enviar essas alterações.|Alfred||Marketing|  
|Usuário2 já tiver enviado essas alterações.||Mary|Serviço|  
  
 User1 decidir resolver esse conflito substituindo valores de base de dados com os valores atuais do membro de cliente.  
  
 Quando User1 resolver o conflito usando <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, o resultado na base de dados é como na tabela a seguir:  
  
||Manager|Assistente|Departamento|  
|------|-------------|---------------|----------------|  
|Novo estado após a resolução do conflito.|Alfred<br /><br /> (de User1)|Maria<br /><br /> (original)|Marketing<br /><br /> (de User1)|  
  
 O código exemplo a seguir mostra como substituir valores de base de dados com os valores atuais do membro de cliente. (Nenhuma inspeção ou manipulação personalizada de conflitos de membro individual ocorrem.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Gerenciar conflitos de alterações](how-to-manage-change-conflicts.md)
