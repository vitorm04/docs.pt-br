---
title: "Chamadas de método locais"
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
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d652072d5f2e0e0cfc74d627b573389864bca9dc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="local-method-calls"></a>Chamadas de método locais
Um chamada de método local é uma chamada que é executada dentro do modelo do objeto. Um chamada de método remoto é uma chamada que o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte no SQL e passa para o mecanismo de banco de dados para execução. Chamadas de método locais são necessários quando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não é possível converter a chamada para SQL. Caso contrário, um <xref:System.InvalidOperationException> será gerado.  
  
## <a name="example-1"></a>Exemplo 1  
 No exemplo a seguir, uma classe `Order` é mapeada para a tabela Orders no banco de dados de exemplo Northwind. Um método de instância local foi adicionado à classe.  
  
 Em Query 1, o construtor da classe `Order` é executado localmente. Na consulta, 2, se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tentou converter `LocalInstanceMethod()`em SQL, a tentativa falhará e um <xref:System.InvalidOperationException> exceção será lançada. Mas como [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece suporte para chamadas de método locais consulta2 não lançará uma exceção.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
