---
title: Sincronizando dados para multithreading
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a17eba2f930fda06d643d78c73c117e89ae86928
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="synchronizing-data-for-multithreading"></a>Sincronizando dados para multithreading
Quando vários threads podem fazer chamadas para as propriedades e métodos de um único objeto, é essencial que as chamadas ser sincronizado. Caso contrário, um thread pode interromper o que outro thread está fazendo e o objeto pode ser deixado em um estado inválido. Classe cujos membros são protegidos contra interrupções de tais é chamada de thread-safe.  
  
 O Common Language Infrastructure fornece várias estratégias para sincronizar o acesso à instância e membros estáticos:  
  
-   Regiões de código sincronizado. Você pode usar o <xref:System.Threading.Monitor> classe ou do compilador suporte para esta classe sincronizar apenas o código de bloco que precisa, melhorando o desempenho.  
  
-   Sincronização manual. Você pode usar os objetos de sincronização fornecidos pela biblioteca de classes .NET Framework. Consulte [visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md), que inclui uma discussão sobre o <xref:System.Threading.Monitor> classe.  
  
-   Contextos sincronizados. Você pode usar o <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> para habilitar a sincronização automática, simple para <xref:System.ContextBoundObject> objetos.  
  
-   Classes de coleção no <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace. Essas classes fornecem interno sincronizado adicionar e remover operações. Para obter mais informações, veja [Coleções thread-safe](../../../docs/standard/collections/thread-safe/index.md).  
  
 O common language runtime fornece um modelo de thread em que classes entram em um número de categorias que podem ser sincronizados em uma variedade de maneiras diferentes, dependendo dos requisitos. A tabela a seguir mostra o suporte de sincronização é fornecido para campos e métodos com uma categoria de determinada sincronização.  
  
|Categoria|Campos globais|Campos estáticos|Métodos estáticos|Campos de instância|Métodos de instância|Blocos de código específico|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Nenhuma sincronização|Não|Não|Não|Não|Não|Não|  
|Contexto sincronizado|Não|Não|Não|Sim|Sim|Não|  
|Regiões de código sincronizado|Não|Não|Somente se marcado|Não|Somente se marcado|Somente se marcado|  
|Sincronização manual|Manual|Manual|Manual|Manual|Manual|Manual|  
  
## <a name="no-synchronization"></a>Nenhuma sincronização  
 Esse é o padrão para objetos. Qualquer thread pode acessar qualquer método ou campo a qualquer momento. Apenas um segmento por vez deve acessar esses objetos.  
  
## <a name="manual-synchronization"></a>Sincronização manual  
 A biblioteca de classes do .NET Framework fornece um número de classes de sincronização de threads. Consulte [visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Regiões de código sincronizado  
 Você pode usar o <xref:System.Threading.Monitor> classe ou uma palavra-chave do compilador para sincronizar os blocos de código, métodos de instância e métodos estáticos. Não há nenhum suporte para campos estáticos sincronizados.  
  
 Visual Basic e c# oferecem suporte a marcação de blocos de código com uma palavra-chave de idioma específico, o `lock` instrução em c# ou o `SyncLock` instrução no Visual Basic. Quando o código é executado por um thread, é feita uma tentativa para adquirir o bloqueio. Se o bloqueio já tiver sido adquirido por outro thread, os blocos de thread até que o bloqueio esteja disponível. Quando o thread sai do bloco sincronizado de código, o bloqueio é liberado, independentemente de como o thread sai do bloco.  
  
> [!NOTE]
>  O `lock` e `SyncLock` instruções são implementadas usando <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, para os outros métodos de <xref:System.Threading.Monitor> pode ser usado em conjunto com-los dentro da região sincronizado.  
  
 Você também pode decorar um método com um **MethodImplAttribute** e **MethodImplOptions**, que tem o mesmo efeito que usar **Monitor** ou do compilador palavras-chave para bloquear todo o corpo do método.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>pode ser usado para interromper um thread de bloqueio de operações, como aguardar o acesso a uma região sincronizado de código. **Thread.Interrupt** também é usada para romper threads fora de operações, como <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Não bloquear o tipo — ou seja, `typeof(MyType)` em c#, `GetType(MyType)` no Visual Basic, ou `MyType::typeid` em C++ — para proteger `static` métodos (`Shared` métodos no Visual Basic). Use um objeto estático particular. Da mesma forma, não use `this` em c# (`Me` no Visual Basic) para métodos de instância de bloqueio. Use um objeto particular. Uma classe ou instância pode ser bloqueada por código diferente de sua preferência, potencialmente causando deadlocks ou problemas de desempenho.  
  
### <a name="compiler-support"></a>Suporte do compilador  
 Visual Basic e c# oferecem suporte a uma palavra-chave do idioma que usa <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> para bloquear o objeto. Visual Basic oferece suporte a [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instrução; C# oferece suporte a [bloqueio](~/docs/csharp/language-reference/keywords/lock-statement.md) instrução.  
  
 Em ambos os casos, se uma exceção é gerada no código do bloco, o bloqueio adquirido pelo **bloqueio** ou **SyncLock** é liberada automaticamente. Os compiladores c# e Visual Basic emitir uma **tente**/**finalmente** bloco com **monitor. ENTER** no início de try, e **Exit**  no **finalmente** bloco. Se uma exceção é gerada dentro de **bloqueio** ou **SyncLock** bloco, o **finalmente** manipulador é executado para que você possa executar qualquer trabalho de limpeza.  
  
## <a name="synchronized-context"></a>Contexto sincronizado  
 Você pode usar o **SynchronizationAttribute** em qualquer **ContextBoundObject** para sincronizar todos os campos e métodos de instância. Todos os objetos no mesmo domínio de contexto compartilham o mesmo bloqueio. Vários threads têm permissão para acessar os métodos e campos, mas apenas um único thread é permitido a qualquer momento.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
 [Threads e threading](../../../docs/standard/threading/threads-and-threading.md)  
 [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 [Instrução SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
 [Instrução lock](~/docs/csharp/language-reference/keywords/lock-statement.md)
