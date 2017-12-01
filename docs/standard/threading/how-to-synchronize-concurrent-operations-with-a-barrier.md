---
title: "Como sincronizar operações simultâneas com uma barreira"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Como sincronizar operações simultâneas com uma barreira
O exemplo a seguir mostra como sincronizar tarefas simultâneas com uma <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Exemplo  
 A finalidade do programa a seguir é para contar o número de iterações (ou fases) são necessários dois threads para cada localização sua metade da solução na mesma fase usando um algoritmo aleatório para rearranjas essas palavras. Após cada thread tem embaralhado seus palavras, a operação de pós-fase de barreira compara os dois resultados para ver se a frase completa foi renderizado na ordem correta do word.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 Um <xref:System.Threading.Barrier> é um objeto que impede que as tarefas individuais em uma operação paralela continue até que todas as tarefas a barreira de alcance. É útil quando ocorre uma operação paralela em fases, e cada fase requer sincronização entre tarefas. Neste exemplo, há duas fases para a operação. A primeira fase, cada tarefa preenche sua seção de buffer com dados. Quando cada tarefa termina de preencher sua seção, a tarefa sinaliza a barreira que ele está pronto para continuar e, em seguida, aguarda. Quando todas as tarefas têm sinalizado a barreira, elas são desbloqueadas e inicia a segunda fase. A barreira é necessária porque a segunda fase requer que cada tarefa tem acesso a todos os dados que foram gerado para esse ponto. Sem a barreira, as conclusão de tarefas primeiro tente ler de buffers que não tem sido preenchidos ainda por outras tarefas. Você pode sincronizar qualquer número das fases dessa maneira.  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de dados para programação paralela](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
