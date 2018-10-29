---
title: Sincronizando dados para multithreading
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a7561a09b1b47827b3476b5525863503765064f
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842652"
---
# <a name="synchronizing-data-for-multithreading"></a>Sincronizando dados para multithreading
Quando vários threads podem fazer chamadas para as propriedades e métodos de um único objeto, é fundamental que essas chamadas sejam sincronizadas. Caso contrário, um thread pode interromper o que outro thread está fazendo e o objeto pode ser deixado em um estado inválido. Uma classe cujos membros são protegidos de tais interrupções é denominada thread-safe.  
  
 A Common Language Infrastructure fornece várias estratégias para sincronizar o acesso à instância e membros estáticos:  
  
-   Regiões de código sincronizadas. Você pode usar o suporte de compilador ou classe <xref:System.Threading.Monitor> para esta classe para sincronizar apenas o bloco de código que precisa, melhorando o desempenho.  
  
-   Sincronização manual. Você pode usar os objetos de sincronização fornecidos pela biblioteca de classes .NET Framework. Confira [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md), que inclui uma discussão sobre a classe <xref:System.Threading.Monitor>.  
  
-   Contextos sincronizados. Você pode usar o <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> para habilitar a sincronização simples e automática para objetos <xref:System.ContextBoundObject>.  
  
-   Classes de coleção no namespace <xref:System.Collections.Concurrent?displayProperty=nameWithType>. Essas classes fornecem operações sincronizadas de adição e remoção internas. Para obter mais informações, veja [Coleções thread-safe](../../../docs/standard/collections/thread-safe/index.md).  
  
 O Common Language Runtime fornece um modelo de thread em que as classes se enquadram em uma série de categorias que podem ser sincronizadas de diferentes maneiras, dependendo dos requisitos. A tabela a seguir mostra o suporte de sincronização fornecido para campos e métodos com uma determinada categoria de sincronização.  
  
|Categoria|Campos globais|Campos estáticos|Métodos estáticos|Campos de instância|Métodos de instância|Blocos de código específico|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Sem sincronização|Não|Não|Não|Não|Não|Não|  
|Contexto sincronizado|Não|Não|Não|Sim|Sim|Não|  
|Regiões de código sincronizadas|Não|Não|Somente se marcado|Não|Somente se marcado|Somente se marcado|  
|Sincronização manual|Manual|Manual|Manual|Manual|Manual|Manual|  
  
## <a name="no-synchronization"></a>Sem sincronização  
 Este é o padrão para objetos. Qualquer thread pode acessar qualquer método ou campo a qualquer momento. Apenas um thread por vez deve acessar esses objetos.  
  
## <a name="manual-synchronization"></a>Sincronização manual  
 A biblioteca de classes do .NET Framework fornece uma série de classes para sincronizar threads. Confira [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Regiões de código sincronizadas  
 Você pode usar a classe <xref:System.Threading.Monitor> ou uma palavra-chave do compilador para sincronizar blocos de código, métodos de instância e métodos estáticos. Não há suporte para campos estáticos sincronizados.  
  
 Tanto o Visual Basic quanto o C # dão suporte à marcação de blocos de código com uma palavra-chave de idioma específica, a instrução `lock` em C # ou a instrução `SyncLock` no Visual Basic. Quando o código é executado por um thread, uma tentativa é feita para adquirir o bloqueio. Se o bloqueio já foi adquirido por outro thread, o thread bloqueia até que o bloqueio fique disponível. Quando o thread sai do bloco de código sincronizado, o bloqueio é liberado, não importa como o thread sai do bloco.  
  
> [!NOTE]
>  As instruções `lock` e `SyncLock` são implementadas usando <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, então outros métodos de <xref:System.Threading.Monitor> podem ser usados em conjunto com eles dentro da região sincronizada.  
  
 Você também pode decorar um método com **MethodImplAttribute** e **MethodImplOptions.Synchronized**, que tem o mesmo efeito que usar **Monitor** ou uma das palavras-chave do compilador para bloquear todo o corpo do método.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> pode ser usado para interromper um thread fora das operações de bloqueio, como aguardar o acesso a uma região de código sincronizada. **Thread.Interrupt** também é usado para interromper threads fora das operações, como <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Não bloqueie o tipo — isto é, `typeof(MyType)` no C#, `GetType(MyType)` no Visual Basic, ou `MyType::typeid` no C++ — para proteger métodos `static` (métodos `Shared` no Visual Basic). Use um objeto estático privado em vez disso. Da mesma forma, não use `this` no C # (`Me` no Visual Basic) para bloquear métodos de instância. Use um objeto privado em vez disso. Uma classe ou instância pode ser bloqueada por código diferente do seu, potencialmente causando deadlocks ou problemas de desempenho.  
  
### <a name="compiler-support"></a>Suporte de compilador  
 O Visual Basic e o C# dão suporte a uma palavra-chave de idioma que usa <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> para bloquear o objeto. O Visual Basic oferece suporte à instrução [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md); C# oferece suporte à instrução [lock](~/docs/csharp/language-reference/keywords/lock-statement.md).  
  
 Em ambos os casos, se uma exceção for lançada no bloqueio de código, o bloqueio adquirido por **lock** ou **SyncLock** é liberado automaticamente. Os compiladores C # e Visual Basic emitem um bloqueio **try**/**finally** com **Monitor.Enter** no início da tentativa, e **Monitor.Exit** no bloqueio **finally**. Se uma exceção for lançada dentro do bloqueio **lock** ou **SyncLock**, o manipulador **finally** é executado para permitir que você faça qualquer trabalho de limpeza.  
  
## <a name="synchronized-context"></a>Contexto sincronizado  
 Você pode usar o **SynchronizationAttribute** em qualquer **ContextBoundObject** para sincronizar todos os métodos e campos da instância. Todos os objetos no mesmo domínio de contexto compartilham o mesmo bloqueio. Múltiplos threads podem acessar os métodos e os campos, mas somente um único thread é permitido em qualquer momento.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
- [Threads e threading](../../../docs/standard/threading/threads-and-threading.md)  
- [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
- [Instrução SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
- [Instrução lock](~/docs/csharp/language-reference/keywords/lock-statement.md)
