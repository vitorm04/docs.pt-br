---
title: Chamadas de método locais
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: ec288d5ac2f6466860362be82c619c89204e8f31
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781427"
---
# <a name="local-method-calls"></a>Chamadas de método locais
Um chamada de método local é uma chamada que é executada dentro do modelo do objeto. Um chamada de método remoto é uma chamada que o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte no SQL e passa para o mecanismo de banco de dados para execução. As chamadas de método local são [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] necessárias quando o não pode converter a chamada em SQL. Caso contrário, um <xref:System.InvalidOperationException> será gerado.  
  
## <a name="example-1"></a>Exemplo 1  
 No exemplo a seguir, uma classe `Order` é mapeada para a tabela Orders no banco de dados de exemplo Northwind. Um método de instância local foi adicionado à classe.  
  
 Em Query 1, o construtor da classe `Order` é executado localmente. Na consulta 2, se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] você tentou traduzir `LocalInstanceMethod()`no SQL, a tentativa falharia e uma <xref:System.InvalidOperationException> exceção seria gerada. Mas como [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o fornece suporte para chamadas de método local, o Query2 não lançará uma exceção.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Informações gerais](background-information.md)
