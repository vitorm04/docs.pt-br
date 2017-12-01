---
title: Mutexes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1d69c1b943d15b9ad8c80b4d7dbafebc54990ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="mutexes"></a>Mutexes
Você pode usar um <xref:System.Threading.Mutex> objeto para fornecer acesso exclusivo a um recurso. O <xref:System.Threading.Mutex> classe usa mais recursos do sistema que o <xref:System.Threading.Monitor> classe, mas pode ser empacotado nos limites do domínio de aplicativo, ele pode ser usado com vários esperas e ele pode ser usado para sincronizar threads em diferentes processos. Para obter uma comparação dos mecanismos de sincronização gerenciado, consulte [visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Para obter exemplos de código, consulte a documentação de referência para o <xref:System.Threading.Mutex.%23ctor%2A> construtores.  
  
## <a name="using-mutexes"></a>Usando Mutexes  
 Um thread chama o <xref:System.Threading.WaitHandle.WaitOne%2A> método de um mutex para a propriedade de solicitação. Os blocos de chamada até que o mutex está disponível ou até que o intervalo de tempo limite opcional expira. O estado de um mutex é sinalizado se nenhum segmento proprietário.  
  
 Um thread libera um mutex chamando seu <xref:System.Threading.Mutex.ReleaseMutex%2A> método. Mutexes têm afinidade de thread; ou seja, o mutex pode ser liberado somente pela thread em que o possui. Se um thread liberar um mutex não possui, um <xref:System.ApplicationException> é gerada no thread.  
  
 Porque o <xref:System.Threading.Mutex> classe derivada de <xref:System.Threading.WaitHandle>, você também pode chamar estático <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> métodos de <xref:System.Threading.WaitHandle> a propriedade de solicitação de um <xref:System.Threading.Mutex> em combinação com outros identificadores de espera.  
  
 Se um thread possui um <xref:System.Threading.Mutex>, thread pode especificar o mesmo <xref:System.Threading.Mutex> em chamadas repetidas de solicitação de espera sem bloquear a execução; no entanto, ele deve liberar o <xref:System.Threading.Mutex> quantas vezes para liberar a propriedade.  
  
## <a name="abandoned-mutexes"></a>Mutexes abandonado  
 Se um thread termina sem soltar um <xref:System.Threading.Mutex>, diz-se o mutex abandonado. Isso geralmente indica um erro grave de programação porque o recurso que está protegendo o mutex poderão ser deixado em um estado inconsistente. No .NET Framework versão 2.0, um <xref:System.Threading.AbandonedMutexException> é lançada no próximo thread que adquire o mutex.  
  
> [!NOTE]
>  Nas versões do .NET Framework 1.0 e 1.1, um abandonado <xref:System.Threading.Mutex> está definido como o estado sinalizado e a próxima aguardando thread obtém propriedade. Se nenhum thread está aguardando, o <xref:System.Threading.Mutex> permanece em um estado sinalizado. Nenhuma exceção é lançada.  
  
 No caso de um mutex de todo o sistema, um mutex abandonado pode indicar que um aplicativo foi finalizado abruptamente (por exemplo, usando o Gerenciador de tarefas do Windows).  
  
## <a name="local-and-system-mutexes"></a>Local e o sistema Mutexes  
 Mutexes são de dois tipos: mutexes local e mutexes sistema nomeado. Se você criar um <xref:System.Threading.Mutex> usando um construtor que aceita um nome de objeto é associado um objeto de sistema operacional do nome. Chamado sistema mutexes são visíveis em todo o sistema operacional e pode ser usados para sincronizar as atividades de processos. Você pode criar várias <xref:System.Threading.Mutex> objetos que representam a mesma chamada de mutex do sistema, e você pode usar o <xref:System.Threading.Mutex.OpenExisting%2A> mutex do sistema de chamada de método para abrir um existente.  
  
 Um mutex local existe somente em seu processo. Ele pode ser usado por qualquer thread no processo que tem uma referência ao local <xref:System.Threading.Mutex> objeto. Cada <xref:System.Threading.Mutex> objeto é um mutex local separado.  
  
### <a name="access-control-security-for-system-mutexes"></a>Segurança de controle de acesso para o sistema Mutexes  
 O .NET Framework versão 2.0 fornece a capacidade de consultar e definir a segurança de controle de acesso do Windows para objetos de sistema nomeado. Proteger o sistema mutexes desde o momento da criação é recomendado porque objetos do sistema são globais e, portanto, podem ser bloqueados pelo código que não seja o seu próprio.  
  
 Para obter informações sobre segurança de controle de acesso para mutexes, consulte o <xref:System.Security.AccessControl.MutexSecurity> e <xref:System.Security.AccessControl.MutexAccessRule> classes, o <xref:System.Security.AccessControl.MutexRights> enumeração, o <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, e <xref:System.Threading.Mutex.OpenExisting%2A> métodos do <xref:System.Threading.Mutex> classe e o <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> construtor.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [Threading](../../../docs/standard/threading/index.md)  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Monitores](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [Threads e threading](../../../docs/standard/threading/threads-and-threading.md)
