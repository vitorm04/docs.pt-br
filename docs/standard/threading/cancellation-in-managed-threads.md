---
title: Cancelamento em threads gerenciados
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
helpviewer_keywords: cancellation in .NET, overview
ms.assetid: eea11fe5-d8b0-4314-bb5d-8a58166fb1c3
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 819f564b93d54c41b879fbfcb20997a8abdebc6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cancellation-in-managed-threads"></a>Cancelamento em threads gerenciados
Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o .NET Framework usa um modelo unificado cooperativo cancelamento de operações síncronas de longa execução ou assíncronas. Esse modelo é baseado em um objeto leve chamado um token de cancelamento. O objeto que invoca uma ou mais operações pode ser canceladas, por exemplo, criando novos threads ou tarefas, passa o token para cada operação. As operações individuais por sua vez podem passar cópias do token para outras operações. Posteriormente, o objeto que criou o token pode usá-lo para solicitar que as operações de param o que eles estão fazendo. Apenas o objeto solicitante pode emitir a solicitação de cancelamento e cada ouvinte é responsável por perceba a solicitação e resposta a ele de maneira oportuna e apropriada.  
  
 O padrão geral para implementar o modelo de cancelamento cooperativo é:  
  
-   Criar uma instância de um <xref:System.Threading.CancellationTokenSource> objeto, que gerencia e envia uma notificação de cancelamento para os tokens de cancelamento individuais.  
  
-   Passe o token retornado pelo <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> propriedade para cada tarefa ou o thread de escuta de cancelamento.  
  
-   Fornecem um mecanismo para cada tarefa ou o thread responder ao cancelamento.  
  
-   Chamar o <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> método para fornecer notificação de cancelamento.  
  
> [!IMPORTANT]
>  A classe <xref:System.Threading.CancellationTokenSource> implementa a interface <xref:System.IDisposable>. Verifique se chamar o <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> método quando você terminar de usar a origem do token de cancelamento para liberar qualquer os recursos que ela contém não gerenciados.  
  
 A ilustração a seguir mostra a relação entre uma origem de token e todas as cópias do seu token.  
  
 ![Tokens de cancelamento e de CancellationTokenSource](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 O novo modelo de cancelamento torna mais fácil criar bibliotecas e aplicativos com reconhecimento de cancelamento e suporta os seguintes recursos:  
  
-   Cancelamento é cooperativo e não será forçado no ouvinte. O ouvinte determina como encerre normalmente em resposta a uma solicitação de cancelamento.  
  
-   Solicitando é diferente de escuta. Um objeto que chama uma operação cancelável pode controlar quando (e se) cancelamento é solicitado.  
  
-   O objeto solicitante emite a solicitação de cancelamento de todas as cópias do token usando apenas um método de chamada.  
  
-   Um ouvinte pode escutar vários tokens simultaneamente unindo-los em uma *token vinculado*.  
  
-   Código do usuário pode observar e responder a solicitações de cancelamento de código da biblioteca e código de biblioteca pode observar e responder a solicitações de cancelamento do código do usuário.  
  
-   Ouvintes podem ser notificados sobre solicitações de cancelamento de sondagem, registro de retorno de chamada ou aguardando identificadores de espera.  
  
## <a name="cancellation-types"></a>Tipos de cancelamento  
 A estrutura de cancelamento é implementada como um conjunto de tipos relacionados que estão listados na tabela a seguir.  
  
|Nome de tipo|Descrição|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Objeto que cria um token de cancelamento e também emite a solicitação de cancelamento para todas as cópias desse token.|  
|<xref:System.Threading.CancellationToken>|Tipo de valor leve passado para um ou mais ouvintes, normalmente como um parâmetro de método. Ouvintes de monitoram o valor de `IsCancellationRequested` propriedade do token por sondagem, o retorno de chamada ou o identificador de espera.|  
|<xref:System.OperationCanceledException>|Sobrecargas de construtor desta exceção aceitarem um <xref:System.Threading.CancellationToken> como um parâmetro. Ouvintes de, opcionalmente, podem gerar essa exceção para verificar se a fonte de cancelamento e notificar outras pessoas que respondeu a uma solicitação de cancelamento.|  
  
 O novo modelo de cancelamento é integrado ao [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] em vários tipos. São os mais importantes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> e <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>. É recomendável que você use esse novo modelo de cancelamento para todos os novo código de aplicativo e de biblioteca.  
  
## <a name="code-example"></a>Exemplo de código  
 No exemplo a seguir cria o objeto solicitando uma <xref:System.Threading.CancellationTokenSource> objeto e, em seguida, passa seu <xref:System.Threading.CancellationTokenSource.Token%2A> propriedade para a operação cancelável. A operação que recebe a solicitação monitora o valor de <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade do token por meio de sondagem. Quando o valor se torna `true`, o ouvinte pode finalizar de maneira que for apropriada. Neste exemplo, o método apenas sai, que é tudo o que é necessário em muitos casos.  
  
> [!NOTE]
>  O exemplo usa o <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> método para demonstrar que a nova estrutura de cancelamento é compatível com APIs herdado. Para obter um exemplo que usa o novo, preferencial <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> de tipo, consulte [como: Cancelar uma tarefa e seus filhos](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Cancelamento da operação em vez de cancelamento do objeto  
 A nova estrutura de cancelamento, cancelamento refere-se a operações, não os objetos. A solicitação de cancelamento significa que a operação deve ser interrompida assim que possível após qualquer limpeza necessária é executada. Um token de cancelamento deve consultar uma "operação cancelável", no entanto, essa operação pode ser implementada em seu programa. Após o <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade do token foi definida `true`, ela não pode ser redefinida para `false`. Portanto, os tokens de cancelamento não podem ser reutilizados depois que eles foram cancelados.  
  
 Se você precisar de um mecanismo de cancelamento do objeto, você pode baseá-la no mecanismo de cancelamento de operação chamando o <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> método, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Se um objeto oferece suporte a mais de uma operação cancelável simultânea, passe um token separado como entrada para cada operação cancelável distinta. Dessa forma, uma operação pode ser cancelada sem afetar os outros.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Escutando e respondendo a solicitações de cancelamento  
 O representante de usuário, o implementador de uma operação cancelável determina como encerrar a operação em resposta a uma solicitação de cancelamento. Em muitos casos, o representante de usuário pode simplesmente executar qualquer limpeza necessária e, em seguida, retornar imediatamente.  
  
 No entanto, em casos mais complexos, pode ser necessário para o representante de usuário notificar o código da biblioteca que o cancelamento tenha ocorrido. Nesses casos, a maneira correta de encerrar a operação é para o representante chamar o <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, método, o que fará com que um <xref:System.OperationCanceledException> seja gerada. Código de biblioteca pode tratar essa exceção no thread de delegado do usuário e examine o token da exceção para determinar se a exceção indica cancelamento cooperativo ou alguma outra situação excepcional.  
  
 O <xref:System.Threading.Tasks.Task> identificadores de classe <xref:System.OperationCanceledException> dessa maneira. Para obter mais informações, consulte [Cancelamento de tarefas](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Escutando por meio de sondagem  
 Para cálculos de longa execução esse loop ou recurse, você pode monitorar uma solicitação de cancelamento consultando periodicamente o valor de <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> propriedade. Se o valor for `true`, o método deve limpar e encerrar o mais rápido possível. A frequência de sondagem de ideal depende do tipo de aplicativo. É responsabilidade do desenvolvedor para determinar a melhor frequência qualquer determinado programa de sondagem. Sondagem em si não afeta o desempenho significativamente. O exemplo a seguir mostra uma maneira possível de sondagem.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Para obter um exemplo mais completo, consulte [como: escutar solicitações de cancelamento por sondagem](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Escutando Registrando um retorno de chamada  
 Algumas operações podem ser bloqueadas de forma que eles não é possível verificar o valor do token de cancelamento de maneira oportuna. Nesses casos, você pode registrar um método de retorno de chamada que desbloqueia o método quando uma solicitação de cancelamento é recebida.  
  
 O <xref:System.Threading.CancellationToken.Register%2A> método retorna um <xref:System.Threading.CancellationTokenRegistration> objeto que é usado especificamente para essa finalidade. O exemplo a seguir mostra como usar o <xref:System.Threading.CancellationToken.Register%2A> método para cancelar uma solicitação da Web assíncrona.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 O <xref:System.Threading.CancellationTokenRegistration> objeto gerencia a sincronização de thread e garante que o retorno de chamada interromperá a execução em um ponto preciso no tempo.  
  
 Para garantir a capacidade de resposta do sistema e para evitar deadlocks, as diretrizes a seguir devem ser seguidas ao registrar retornos de chamada:  
  
-   O método de retorno de chamada deve ser rápido porque ele é chamado síncrona e, portanto, a chamada para <xref:System.Threading.CancellationTokenSource.Cancel%2A> não retorna até que o retorno de chamada retorne.  
  
-   Se você chamar <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> enquanto o retorno de chamada está em execução e manter um bloqueio que está aguardando o retorno de chamada, o programa pode deadlock. Depois de `Dispose` retornar, você pode liberar todos os recursos necessários para o retorno de chamada.  
  
-   Retornos de chamada não deverá efetuar qualquer thread manual ou <xref:System.Threading.SynchronizationContext> uso em um retorno de chamada. Se um retorno de chamada deve ser executado em um segmento específico, use o <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> construtor que permite que você especificar que o destino syncContext está ativo <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>. Execução de threading manual em um retorno de chamada pode causar deadlock.  
  
 Para obter um exemplo mais completo, consulte [como: registrar retornos de chamada para solicitações de cancelamento](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Escutando usando um identificador de espera  
 Quando uma operação cancelável pode bloquear ao aguardar uma sincronização primitiva, como um <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> ou <xref:System.Threading.Semaphore?displayProperty=nameWithType>, você pode usar o <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> propriedade para habilitar a aguardar o evento e a solicitação de cancelamento da operação. O identificador de espera do token de cancelamento será tornou-se sinalizado em resposta a uma solicitação de cancelamento e o método pode usar o valor de retorno de <xref:System.Threading.WaitHandle.WaitAny%2A> método para determinar se ele foi o cancelamento de token que sinalizado. A operação poderá, em seguida, simplesmente sair ou lançar um <xref:System.OperationCanceledException>, conforme apropriado.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 Novo código que tem como alvo o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> e <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> oferecem suporte a nova estrutura de cancelamento em seus `Wait` métodos. Você pode passar o <xref:System.Threading.CancellationToken> para o método, e quando o cancelamento for solicitado, o evento é acionado e gera um <xref:System.OperationCanceledException>.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Para obter um exemplo mais completo, consulte [como: escutar solicitações de cancelamento que têm espera manipula](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Escutando simultaneamente para vários Tokens  
 Em alguns casos, pode ter um ouvinte escutar simultaneamente vários tokens de cancelamento. Por exemplo, uma operação cancelável pode ter que monitorar um token de cancelamento interno, além de um token passado externamente como um argumento para um parâmetro de método. Para fazer isso, crie uma fonte de token vinculada que pode unir duas ou mais símbolos em um token, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Observe que você deve chamar `Dispose` sobre a origem do token vinculada quando tiver terminado com ele. Para obter um exemplo mais completo, consulte [como: ouvir várias solicitações de cancelamento](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Cooperação entre o código de biblioteca e o código do usuário  
 A estrutura de cancelamento unificada torna possível para o código de biblioteca cancelar o código do usuário e código de usuário cancelar o código da biblioteca de forma cooperativa. Cooperação Smooth depende de cada lado estas diretrizes:  
  
-   Se o código da biblioteca fornece operações anulável, ela também deve fornecer métodos públicos que aceitam um token de cancelamento externo para que o código do usuário pode solicitar o cancelamento.  
  
-   Se chamar o código de biblioteca no código de usuário, o código de biblioteca deve interpretar um OperationCanceledException(externalToken) como *cancelamento cooperativo*e não necessariamente uma exceção de falha.  
  
-   Representantes do usuário devem tentar responder a solicitações de cancelamento de código da biblioteca de maneira oportuna.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>e <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> são exemplos de classes que segue essas diretrizes. Para obter mais informações, consulte [cancelamento da tarefa](../../../docs/standard/parallel-programming/task-cancellation.md)e [como: Cancelar uma consulta PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas de threading gerenciado](../../../docs/standard/threading/managed-threading-basics.md)
