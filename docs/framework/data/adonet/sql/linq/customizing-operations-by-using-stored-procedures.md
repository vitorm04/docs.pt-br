---
title: "Personalizando operações usando procedimentos armazenados"
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
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 105f52b61d6b5c0b05bd08a9a1f6b1c07f94226d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Personalizando operações usando procedimentos armazenados
Os procedimentos armazenados representam uma abordagem mais comum para substituir o comportamento padrão. Os exemplos neste tópico mostram como você pode usar wrappers gerados do método para procedimentos armazenados, e como você pode chamar procedimentos armazenados diretamente.  
  
 Se você estiver usando [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], você pode usar [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para atribuir procedimentos armazenados, executar inserções, atualizações e exclusões.  
  
> [!NOTE]
>  Para ler valores base de dados - gerados novamente, use parâmetros de saída em seus procedimentos armazenados. Se você não pode usar parâmetros de saída, escreva uma implementação de método parcial em vez de depender nas substituições geradas por [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Os membros mapeados para os valores base de dados - gerados devem ser definidos para apropriado valores depois que `INSERT` ou operações de `UPDATE` terminar com êxito. Para obter mais informações, consulte [responsabilidades do desenvolvedor em Substituir padrão comportamento](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 No exemplo, presuma que a classe de `Northwind` contém dois métodos para chamar procedimentos armazenados que estão sendo usados para alternativas em uma classe derivada.  
  
### <a name="code"></a>Código  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 A classe seguir usa esses métodos para substituição.  
  
### <a name="code"></a>Código  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Você pode usar `NorthwindThroughSprocs` exatamente como você usaria `Northwnd`.  
  
### <a name="code"></a>Código  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 [Responsabilidades do desenvolvedor em substituir o comportamento padrão](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
