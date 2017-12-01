---
title: "Threading gerenciado e não gerenciado no Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c55caaff3fd96b2791e75a392a9522abfceb22e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Threading gerenciado e não gerenciado no Windows
O gerenciamento de todos os threads, inclusive de threads criados pelo Common Language Runtime e fora do tempo de execução que ingressam no ambiente gerenciado para executar o código, é feito pela classe <xref:System.Threading.Thread>. O tempo de execução monitora todos os threads de seu processo que já executaram o código no ambiente de execução gerenciado. Ele não rastreia nenhum outro thread. Threads podem entrar no ambiente de execução gerenciado por meio de interoperabilidade COM (porque o tempo de execução expõe objetos gerenciados como objetos COM o mundo não gerenciado), o COM [DllGetClassObject](https://msdn.microsoft.com/en-us/library/ms680760.aspx) função e a invocação de plataforma.  
  
 Quando um thread não gerenciado entra em tempo de execução por meio de, por exemplo, um COM callable wrapper, o sistema verifica o armazenamento local de thread desse thread para procurar gerenciados interno <xref:System.Threading.Thread> objeto. Caso o sistema encontre um thread desse tipo, o tempo de execução fica ciente sobre ele. Se ele não é possível encontrar um, no entanto, o tempo de execução cria um novo <xref:System.Threading.Thread> de objeto e instala-o no armazenamento local de thread do thread.  
  
 Gerenciado em processos, <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> é a identificação do thread gerenciado estável. Durante seu tempo de vida, o thread não colidirá com os valores de outros threads, independente do domínio do aplicativo para o qual você obtém esse valor.  
  
> [!NOTE]
>  Um sistema operacional **ThreadId** não tem nenhuma relação fixa a um thread gerenciado, como um host não gerenciado pode controlar a relação entre os threads gerenciados e não gerenciados. Mais especificamente, hosts sofisticados podem usar a API Fiber para agendar muitos threads gerenciados no mesmo thread do sistema operacional ou para mover um thread gerenciado por diferentes threads do sistema operacional.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapeando do threading do Win32 para o threading gerenciado  
 A tabela a seguir mapeia os elementos do threading do Win32 com seu equivalente aproximado no tempo de execução. Esse mapeamento não representa uma funcionalidade idêntica. Por exemplo, **TerminateThread** não executa **finalmente** cláusulas ou libere recursos e não podem ser impedidos. No entanto, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> executa todo o código de reversão, recupera todos os recursos e pode ser negado com <xref:System.Threading.Thread.ResetAbort%2A>. Leia a documentação com atenção e não faça deduções sobre a funcionalidade.  
  
|No Win32|No Common Language Runtime|  
|--------------|------------------------------------|  
|**CreateThread**|Combinação de **Thread** e<xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Sleep**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** no identificador de thread|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Não há equivalência|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Não há equivalência|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Não há equivalência|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Fechar para **CoInitializeEx** (OLE32. DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Threads gerenciados e apartments COM  
 Um thread gerenciado pode ser marcado para indicar que ele irá hospedar um [single-threaded](http://msdn.microsoft.com/library/windows/desktop/ms680112.aspx) ou [multithread](http://msdn.microsoft.com/library/windows/desktop/ms693421.aspx) apartment. (Para obter mais informações sobre o COM threading arquitetura, consulte [processos, threads e Apartments](http://msdn.microsoft.com/library/windows/desktop/ms693344.aspx).) Os métodos <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A> e <xref:System.Threading.Thread.TrySetApartmentState%2A> da classe <xref:System.Threading.Thread> retornam e atribuem o estado de apartment de um thread. Se o estado não tiver sido definido, <xref:System.Threading.Thread.GetApartmentState%2A> retorna <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 A propriedade pode ser definida somente quando o thread está no <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> estado; ela pode ser definida apenas uma vez por um thread.  
  
 Se o estado do apartment não for definido antes do início do thread, o thread será iniciado como MTA (multithreaded apartment). O thread finalizador e todos os threads controlados por <xref:System.Threading.ThreadPool> são do tipo MTA.  
  
> [!IMPORTANT]
>  No caso do código de inicialização do aplicativo, a única forma de controlar o estado do apartment é aplicar <xref:System.MTAThreadAttribute> ou <xref:System.STAThreadAttribute> ao procedimento do ponto de entrada. No .NET Framework 1.0 e 1.1, você pode definir a propriedade <xref:System.Threading.Thread.ApartmentState%2A> como a primeira linha de código. Isso não é permitido no .NET Framework 2.0.  
  
 Os objetos gerenciados que são expostos ao comportamento COM comportam-se como se houvesse um marshaler de thread livre agregado a eles. Em outras palavras, eles podem ser chamados por qualquer apartment COM no modo de threading livre. Os únicos objetos gerenciados que não apresentam esse comportamento são os objetos derivados de <xref:System.EnterpriseServices.ServicedComponent> ou <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 No mundo gerenciado, não há suporte a <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>, a menos que você use contextos e instâncias gerenciadas vinculadas a um contexto. Se você estiver usando os serviços corporativos, o objeto deve ser derivado de <xref:System.EnterpriseServices.ServicedComponent> (que é derivada de <xref:System.ContextBoundObject>).  
  
 Quando o código gerenciado chama objetos COM, ele sempre segue as regras COM. Em outras palavras, ele faz a chamada por meio de proxies de apartment COM e COM+ 1.0 context wrappers, como ditado por OLE32.  
  
## <a name="blocking-issues"></a>Problemas de bloqueio  
 Se um thread fizer uma chamada não gerenciada no sistema operacional que bloqueou o thread no código não gerenciado, o tempo de execução não assumirá o controle para <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nem <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. No caso de <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, marca de tempo de execução do thread para **anular** e assume o controle do mesmo quando ele entrar novamente no código gerenciado. Recomendamos que você use bloqueios gerenciados, em vez de não gerenciados. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>, <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>, e assim por diante são todos responder ao <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> e <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Além disso, se seu thread estiver em um single-threaded apartment, todas essas operações de bloqueio gerenciado enviarão mensagens para seu apartment enquanto o thread estiver bloqueado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>  
 <xref:System.Threading.ThreadState>  
 <xref:System.EnterpriseServices.ServicedComponent>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.Monitor>
