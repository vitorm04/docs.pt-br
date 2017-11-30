---
title: "Como ouvir solicitações de cancelamento por meio de sondagem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f0e05e3f66d591a28d7e84d358934959764dab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Como ouvir solicitações de cancelamento por meio de sondagem
O exemplo a seguir mostra uma maneira que o código do usuário pode sondar um token de cancelamento em intervalos regulares para ver se cancelamento foi solicitado o thread de chamada. Este exemplo usa o <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> tipo, mas o mesmo padrão aplica-se a operações assíncronas criadas diretamente pelo <xref:System.Threading.ThreadPool?displayProperty=nameWithType> tipo ou o <xref:System.Threading.Thread?displayProperty=nameWithType> tipo.  
  
## <a name="example"></a>Exemplo  
 Sondagem requer algum tipo de código de loop ou recursiva que periodicamente pode ler o valor de booliano <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade. Se você estiver usando o <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> tipo e estão aguardando a conclusão no thread de chamada da tarefa, você pode usar o <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> método para verificar a propriedade e lançar a exceção. Usando esse método, você garantir que a exceção correta é gerada em resposta a uma solicitação. Se você estiver usando um <xref:System.Threading.Tasks.Task>, e em seguida, chamar este método é melhor do que gerar manualmente um <xref:System.OperationCanceledException>. Se você não tiver lançar a exceção, basta verificar a propriedade e se a propriedade de retorno do método `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Chamando <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> é extremamente rápido e não apresenta uma sobrecarga significativa em loops.  
  
 Se você estiver chamando <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, você só precisa verificar explicitamente o <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade se você tiver outro trabalho em resposta ao cancelamento além lançando a exceção. Neste exemplo, você pode ver que o código realmente acessa a propriedade duas vezes: uma vez no acesso explícito e novamente no <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> método. Mas, como o ato de leitura de <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade envolve volátil apenas uma instrução por acesso de leitura, o acesso duplo não é significativo de uma perspectiva de desempenho. Ainda é melhor para chamar o método em vez de lançar manualmente a <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Consulte também  
 [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
