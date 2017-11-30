---
title: Coletas induzidas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92918e347b10dfcf3a0d6e2c08cec8c7a6963f5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="induced-collections"></a>Coletas induzidas
Na maioria dos casos, o coletor de lixo pode determinar o melhor momento para executar uma coleta e você deve permitir que ele seja executado de modo independente. Existem situações raras nas quais uma coleta forçada pode melhorar o desempenho do seu aplicativo. Nesses casos, você pode induzir a coleta de lixo usando o <xref:System.GC.Collect%2A?displayProperty=nameWithType> método para forçar uma coleta de lixo.  
  
 Use o <xref:System.GC.Collect%2A?displayProperty=nameWithType> método quando não houver uma redução significativa na quantidade de memória que está sendo usada em um ponto específico no código do aplicativo. Por exemplo, se seu aplicativo usa uma caixa de diálogo complexas que tenha vários controles, chamar <xref:System.GC.Collect%2A> quando a caixa de diálogo é fechada pode melhorar o desempenho com a recuperação imediatamente a memória usada pela caixa de diálogo. Certifique-se de que seu aplicativo não está induzindo a coleta de lixo com muita frequência, pois isso poderá diminuir o desempenho se o coletor de lixo estiver tentando recuperar os objetos em horários não ideais. Você pode fornecer um <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> valor de enumeração para o <xref:System.GC.Collect%2A> método para coletar somente quando a coleção ser produtiva, conforme discutido na próxima seção.  
  
## <a name="gc-collection-mode"></a>Modo de coleta de GC  
 Você pode usar uma da <xref:System.GC.Collect%2A?displayProperty=nameWithType> sobrecargas do método que inclui um <xref:System.GCCollectionMode> valor para especificar o comportamento de uma coleção forçado da seguinte maneira.  
  
|Valor `GCCollectionMode`|Descrição|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Usa a configuração de coleta de lixo padrão para a versão em execução do .NET.|  
|<xref:System.GCCollectionMode.Forced>|Força a coleta de lixo a ocorrer imediatamente. Isso é equivalente a chamar o <xref:System.GC.Collect?displayProperty=nameWithType> sobrecarga. Isso resulta em uma coleta de bloqueio total de todas as gerações.<br /><br /> Você também pode compactar o heap de objeto grande, definindo o <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> propriedade <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> antes de forçar uma coleta de lixo bloqueio completo imediata.|  
|<xref:System.GCCollectionMode.Optimized>|Permite que o coletor de lixo determine se o horário atual é ideal para recuperar objetos.<br /><br /> O coletor de lixo pode determinar que uma coleta não seria suficientemente produtiva para se justificar, caso em que ele retornará sem recuperar objetos.|  
  
## <a name="background-or-blocking-collections"></a>Coletas de bloqueio ou em segundo plano  
 Você pode chamar o <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> sobrecarga do método para especificar se uma coleção induzida está bloqueando ou não. O tipo de coleção executada depende de uma combinação do método `mode` e `blocking` parâmetros. `mode`é um membro do <xref:System.GCCollectionMode> enumeração e `blocking` é um <xref:System.Boolean> valor. A tabela a seguir resume a interação entre o `mode` e `blocking` argumentos.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> ou <xref:System.GCCollectionMode.Default>|Uma coleção de bloqueio é executada assim que possível. Se uma coleção de plano de fundo está em andamento e geração for 0 ou 1, o <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> método imediatamente dispara uma coleção de bloqueio e retorna quando a coleção é concluída. Se uma coleção de plano de fundo está em andamento e o `generation` parâmetro é 2, o método de espera até que a coleção de plano de fundo é concluída, aciona uma coleção de geração 2 bloqueio e, em seguida, retorna.|Uma coleta é executada assim que possível. O <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> método solicita uma coleção de plano de fundo, mas isso não é garantido; dependendo das circunstâncias, uma coleção de bloqueio ainda pode ser executada. Se uma coleta em segundo plano já estiver em andamento, o método retornará imediatamente.|  
|<xref:System.GCCollectionMode.Optimized>|Uma coleção de bloqueio pode ser executada, dependendo do estado de coletor de lixo e a `generation` parâmetro. O coletor de lixo tenta fornecer um desempenho ideal.|Uma coleta pode ser executada, dependendo do estado do coletor de lixo. O <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> método solicita uma coleção de plano de fundo, mas isso não é garantido; dependendo das circunstâncias, uma coleção de bloqueio ainda pode ser executada. O coletor de lixo tenta fornecer um desempenho ideal. Se uma coleta em segundo plano já estiver em andamento, o método retornará imediatamente.|  
  
## <a name="see-also"></a>Consulte também  
 [Modos de latência](../../../docs/standard/garbage-collection/latency.md)  
 [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
