---
title: "Notificações sobre a coleta de lixo"
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
- cpp
helpviewer_keywords: garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41a2ed9c5d239f1570955e87bb5b749e29830bc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-notifications"></a>Notificações sobre a coleta de lixo
Há situações em que uma coleta de lixo completa (ou seja, uma coleção de geração 2) o common language runtime pode afetar o desempenho. Isso pode ser um problema particularmente com servidores que processam grandes volumes de pedidos; Nesse caso, uma coleta de lixo longa pode causar um tempo limite da solicitação. Para impedir que uma coleção completa de segundo que ocorrem durante um período crítico, você pode ser notificado de que uma coleta de lixo completa está se aproximando e, em seguida, execute a ação para redirecionar a carga de trabalho para outra instância do servidor. Você pode também induzir uma coleção por conta própria, desde que a instância do servidor atual não é necessário processar solicitações.  
  
 O <xref:System.GC.RegisterForFullGCNotification%2A> método registra uma notificação ser gerado quando o tempo de execução detecta que está se aproximando de uma coleta de lixo completa. Há duas partes para esta notificação: quando a coleta de lixo completa está se aproximando e quando a coleta de lixo completa foi concluída.  
  
> [!WARNING]
>  Coletas de lixo de bloqueio somente geram notificações. Quando o [ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) elemento de configuração estiver habilitado, coletas de lixo em segundo plano não vai disparar notificações.  
  
 Para determinar quando uma notificação foi ativada, use o <xref:System.GC.WaitForFullGCApproach%2A> e <xref:System.GC.WaitForFullGCComplete%2A> métodos. Normalmente, você pode usar esses métodos em um `while` loop continuamente obter um <xref:System.GCNotificationStatus> enumeração que mostra o status da notificação. Se esse valor for <xref:System.GCNotificationStatus.Succeeded>, você pode fazer o seguinte:  
  
-   Em resposta a uma notificação obtida com o <xref:System.GC.WaitForFullGCApproach%2A> método, você pode redirecionar a carga de trabalho e possivelmente induzir uma coleção por conta própria.  
  
-   Em resposta a uma notificação obtida com o <xref:System.GC.WaitForFullGCComplete%2A> método, você pode tornar disponíveis para processar solicitações novamente a instância do servidor atual. Você também pode coletar informações. Por exemplo, você pode usar o <xref:System.GC.CollectionCount%2A> método para registrar o número de coleções.  
  
 O <xref:System.GC.WaitForFullGCApproach%2A> e <xref:System.GC.WaitForFullGCComplete%2A> métodos são projetados para trabalhar juntos. Usando um sem o outro pode produzir resultados indeterminados.  
  
## <a name="full-garbage-collection"></a>Coleta de lixo completa  
 O tempo de execução faz com que uma coleta de lixo completa quando qualquer uma das seguintes situações for verdadeira:  
  
-   Memória insuficiente foi promovida na geração 2 para fazer com que a próxima coleta de geração 2.  
  
-   Memória insuficiente foi promovida para o heap de objeto grande para fazer com que a próxima coleta de geração 2.  
  
-   Uma coleção de geração 1 é escalada para uma coleção de geração 2 devido a outros fatores.  
  
 Os limites que você especificar o <xref:System.GC.RegisterForFullGCNotification%2A> método aplicar para os primeiros dois cenários. No entanto, o primeiro cenário você não sempre receberão a notificação ao tempo proporcional para os valores de limite especificados por dois motivos:  
  
-   O tempo de execução não verifica cada alocação de objeto pequeno (por motivos de desempenho).  
  
-   Somente geração 1 coleções promovem memória em geração 2.  
  
 O terceiro cenário também contribui para a incerteza de quando você recebe a notificação. Embora isso não é uma garantia, ele mostrará como uma maneira útil para reduzir os efeitos de uma coleta de lixo completa inoportunos redirecionar as solicitações durante esse tempo ou induzindo coleção por conta própria quando pode ser acomodada melhor.  
  
## <a name="notification-threshold-parameters"></a>Parâmetros de limite de notificação  
 O <xref:System.GC.RegisterForFullGCNotification%2A> método tem dois parâmetros para especificar os valores de limite de objetos da geração 2 e o heap de objeto grande. Quando esses valores forem atendidas, uma notificação de coleta de lixo deve ser gerada. A tabela a seguir descreve esses parâmetros.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Um número entre 1 e 99 que especifica quando a notificação deve ser gerada com base nos objetos promovidos na geração 2.|  
|`largeObjectHeapThreshold`|Um número entre 1 e 99 que especifica quando a notificação deve ser gerada com base nos objetos que são alocados no heap de objeto grande.|  
  
 Se você especificar um valor que é muito alto, há uma alta probabilidade de que você receberá uma notificação, mas pode ser muito um período de espera antes que o tempo de execução faz com que uma coleção. Se você mesmo induzir uma coleção, você pode recuperar mais objetos que seriam recuperados se o tempo de execução faz com que a coleção.  
  
 Se você especificar um valor muito baixo, o tempo de execução pode causar a coleção antes de você ter tido tempo suficiente para ser notificado.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 No exemplo a seguir, um grupo de servidores de serviço as solicitações da Web. Para simular a carga de trabalho de processamento de solicitações, matrizes de bytes são adicionados a um <xref:System.Collections.Generic.List%601> coleção. Cada servidor registra uma notificação de coleta de lixo e, em seguida, inicia um thread no `WaitForFullGCProc` método de usuário para monitorar continuamente o <xref:System.GCNotificationStatus> enumeração que é retornada pelo <xref:System.GC.WaitForFullGCApproach%2A> e <xref:System.GC.WaitForFullGCComplete%2A> métodos.  
  
 O <xref:System.GC.WaitForFullGCApproach%2A> e <xref:System.GC.WaitForFullGCComplete%2A> métodos chamam seus respectivos métodos de usuário de manipulação de eventos quando uma notificação é gerada:  
  
-   `OnFullGCApproachNotify`  
  
     Este método chama o `RedirectRequests` método de usuário, que instrui o servidor de enfileiramento de mensagens de solicitação para suspender a enviar solicitações ao servidor. Isso é simulado, definindo a variável de nível de classe `bAllocate` para `false` para que nenhum outro objeto é alocado.  
  
     Em seguida, o `FinishExistingRequests` usuário método é chamado para concluir o processamento das solicitações pendentes do servidor. Isso é simulado desmarcando a <xref:System.Collections.Generic.List%601> coleção.  
  
     Por fim, uma coleta de lixo seja induzida porque a carga de trabalho é claro.  
  
-   `OnFullGCCompleteNotify`  
  
     Este método chama o método de usuário `AcceptRequests` para retomar a aceitar solicitações porque o servidor não está mais suscetível a coleta de lixo completa. Essa ação é simulada, definindo o `bAllocate` variável para `true` para que objetos podem continuar sendo adicionado ao <xref:System.Collections.Generic.List%601> coleção.  
  
 O código a seguir contém o `Main` método do exemplo.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 O código a seguir contém o `WaitForFullGCProc` método de usuário, que contém um contínua ao loop para verificar se há notificações de coleta de lixo.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 O código a seguir contém o `OnFullGCApproachNotify` método conforme chamado a partir de  
  
 Método `WaitForFullGCProc`.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 O código a seguir contém o `OnFullGCApproachComplete` método conforme chamado a partir de  
  
 Método `WaitForFullGCProc`.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 O código a seguir contém os métodos de usuário que são chamados do `OnFullGCApproachNotify` e `OnFullGCCompleteNotify` métodos. Os métodos de usuário redirecionam as solicitações, concluir as solicitações existentes e, em seguida, continuar solicitações após a coleta de lixo completa.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 O exemplo de código inteira é o seguinte:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
