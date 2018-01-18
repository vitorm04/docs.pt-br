---
title: 'Como: Resolver Conflitos mantendo valores de base de dados'
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
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0747a4318fdab76c5fbd920f7291346d4d8ff58d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Como: Resolver Conflitos mantendo valores de base de dados
Para reconciliar diferenças entre valores esperados e reais de base de dados antes que você submeter tente novamente suas alterações, você pode usar <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> para manter os valores localizados na base de dados. Os valores atuais no modelo de objeto são substituídos em seguida. Para obter mais informações, consulte [simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Em todos os casos, o registro no cliente é atualizado primeiro recuperando os dados atualizados de base de dados. Esta ação certifique-se de que a seguir tentativa de atualização não falhará nas mesmas verificação de simultaneidade.  
  
## <a name="example"></a>Exemplo  
 Nesse cenário, uma exceção é lançada de <xref:System.Data.Linq.ChangeConflictException> quando tenta User1 para enviar alterações, porque Usuário2 tiver alterado entretanto as colunas do assistente e departamento. A tabela a seguir mostra a situação.  
  
||Manager|Assistente|Departamento|  
|------|-------------|---------------|----------------|  
|Estado original de base de dados quando consultado por User1 e por Usuário2.|Alfreds|Maria|Vendas|  
|User1 prepara-se para enviar essas alterações.|Alfred||Marketing|  
|Usuário2 já tiver enviado essas alterações.||Mary|Serviço|  
  
 User1 decidir resolver esse conflito com os valores mais recentes de base de dados substitui os valores atuais no modelo de objeto.  
  
 Quando User1 resolver o conflito usando <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, o resultado na base de dados é o seguinte na tabela:  
  
||Manager|Assistente|Departamento|  
|------|-------------|---------------|----------------|  
|Novo estado após a resolução do conflito.|Alfreds<br /><br /> (original)|Mary<br /><br /> (de Usuário2)|Serviço<br /><br /> (de Usuário2)|  
  
 O código exemplo a seguir mostra como substituir valores atuais no modelo de objeto com os valores de base de dados. (Nenhuma inspeção ou manipulação personalizada de conflitos de membro individual ocorrem.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Como gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
