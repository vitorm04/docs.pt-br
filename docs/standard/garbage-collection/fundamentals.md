---
title: Noções básicas da coleta de lixo
description: Saiba como o coletor de lixo funciona e como ele pode ser configurado para ter um desempenho ideal.
ms.date: 11/15/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background
- garbage collection, concurrent
- garbage collection, server
- garbage collection, workstation
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
ms.openlocfilehash: ea8aef03d2f5837f35ecb31209e57853c0c8257b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330426"
---
# <a name="fundamentals-of-garbage-collection"></a>Noções básicas da coleta de lixo

In the common language runtime (CLR), the garbage collector (GC) serves as an automatic memory manager. Ele oferece os seguintes benefícios:

- Enables you to develop your application without having to manually free memory.

- Aloca objetos no heap gerenciado com eficiência.

- Recupera os objetos que não estão sendo usados, limpa a memória e mantém a memória disponível para alocações futuras. Os objetos gerenciados obtêm automaticamente conteúdo limpo com o qual começar, portanto, seus construtores não precisam inicializar cada campo de dados.

- Fornece segurança de memória, assegurando que um objeto não possa usar o conteúdo de outro objeto.

This article describes the core concepts of garbage collection.

## <a name="fundamentals-of-memory"></a>Conceitos básicos de memória

A lista a seguir resume conceitos importantes de memória do CLR.

- Cada processo tem seu próprio espaço de endereço virtual separado. All processes on the same computer share the same physical memory and the page file, if there is one.

- Por padrão, em computadores de 32 bits, cada processo tem um espaço de endereço virtual no modo de usuário de 2 GB.

- Como desenvolvedor de aplicativos, você trabalha apenas com o espaço de endereço virtual e nunca manipula a memória física diretamente. O coletor de lixo aloca e libera memória virtual para você no heap gerenciado.

  If you are writing native code, you use Windows functions to work with the virtual address space. Essas funções alocam e liberam memória virtual para você em heaps nativos.

- A memória virtual pode estar em três estados:

  - Livre. O bloco de memória não tem referências a ele e está disponível para alocação.

  - Reservado. O bloco de memória está disponível para seu uso e não pode ser usado para nenhuma outra solicitação de alocação. No entanto, você não pode armazenar dados nesse bloco de memória até que ele esteja comprometido.

  - Comprometido. O bloco de memória é atribuído para armazenamento físico.

- O espaço de endereço virtual pode ficar fragmentado. Isso significa que há blocos livres, também conhecido como furos, no espaço de endereço. Quando uma alocação de memória virtual é solicitada, o gerenciador de memória virtual precisa localizar um único bloco livre suficientemente grande para atender a essa solicitação de alocação. Mesmo que você tenha 2 GB de espaço livre, a alocação que exige 2 GB não será bem-sucedida a menos que todo esse espaço livre esteja em um único bloco de endereço.

- You can run out of memory if there isn't enough virtual address space to reserve or physical space to commit.

  The page file is used even if physical memory pressure (that is, demand for physical memory) is low. The first time physical memory pressure is high, the operating system must make room in physical memory to store data, and it backs up some of the data that is in physical memory to the page file. That data is not paged until it's needed, so it's possible to encounter paging in situations where the physical memory pressure is low.

## <a name="conditions-for-a-garbage-collection"></a>Condições para uma coleta de lixo

A coleta de lixo ocorre quando uma das seguintes condições é verdadeira:

- O sistema tem pouca memória física. This is detected by either the low memory notification from the OS or low memory as indicated by the host.

- A memória usada por objetos alocados no heap gerenciado ultrapassa o limite aceitável. Esse limite é ajustado continuamente enquanto o processo é executado.

- O método <xref:System.GC.Collect%2A?displayProperty=nameWithType> é chamado. Em quase todos os casos, você não precisa chamar esse método porque o coletor de lixo funciona continuamente. Esse método é usado principalmente para situações exclusivas e testes.

## <a name="the-managed-heap"></a>O heap gerenciado

Depois que o coletor de lixo é inicializado pelo CLR, ele aloca um segmento da memória para armazenar e gerenciar objetos. Essa memória é chamada de heap gerenciado, em contraposição a um heap nativo no sistema operacional.

Há um heap gerenciado para cada processo gerenciado. Todos os threads no processo alocam memória para objetos no mesmo heap.

To reserve memory, the garbage collector calls the Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) function and reserves one segment of memory at a time for managed applications. The garbage collector also reserves segments, as needed, and releases segments back to the operating system (after clearing them of any objects) by calling the Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) function.

> [!IMPORTANT]
> O tamanho de segmentos alocados pelo coletor de lixo é específico da implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas. Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.

Quanto menos objetos alocados no heap, menos trabalho o coletor de lixo precisa fazer. Ao alocar objetos, não use valores arredondados que excedam suas necessidades, por exemplo, alocando uma matriz de 32 bytes quando são necessários apenas 15 bytes.

Quando uma coleta de lixo é disparada, o coletor de lixo recupera a memória ocupada por objetos inativos. O processo de recuperação compacta objetos vivos para que eles sejam movidos juntos e o espaço inativo é removido, tornando o heap menor. Isso garante que os objetos que são alocados juntos permaneçam juntos no heap gerenciado, para preservar sua localidade.

O grau de intrusão (frequência e a duração) de coletas de lixo é o resultado do volume de alocações e da quantidade de memória restante no heap gerenciado.

O heap pode ser considerado como o acúmulo de dois heaps: o [heap de objetos grandes](large-object-heap.md) e o heap de objetos pequenos.

O [heap de objetos grandes](large-object-heap.md) contém objetos muito grandes, com 85.000 bytes ou mais. Os objetos no heap de objetos grandes normalmente são matrizes. É raro que um objeto de instância seja muito grande.

> [!TIP]
> You can [configure the threshold size](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) for objects to go on the large object heap.

## <a name="generations"></a>Gerações

O heap está organizado em gerações de modo que possa manipular objetos de vida útil longa e curta. A coleta de lixo ocorre principalmente com a recuperação de objetos de vida útil curta, que geralmente ocupam apenas uma pequena parte do heap. Há três gerações de objetos no heap:

- **Geração 0**. Essa é a geração mais jovem e contém objetos de vida útil curta. Um exemplo de um objeto de vida útil curta é uma variável temporária. A coleta de lixo ocorre com mais frequência nessa geração.

  Newly allocated objects form a new generation of objects and are implicitly generation 0 collections. However, if they are large objects, they go on the large object heap in a generation 2 collection.

  A maioria dos objetos são recuperados para coleta de lixo na geração 0 e não sobrevivem para a próxima geração.

- **Geração 1**. Essa geração contém objetos de vida útil curta e serve como um buffer entre objetos de vida útil curta e longa.

- **Geração 2**. Essa geração contém objetos de vida útil longa. An example of a long-lived object is an object in a server application that contains static data that's live for the duration of the process.

Coletas de lixo ocorrem em gerações específicas conforme as condições permitirem. Coletar uma geração significa coletar objetos nessa geração e todas as suas gerações mais jovens. Uma coleta de lixo da geração 2 também é conhecida como uma coleta de lixo completa, pois ela recupera todos os objetos em todas as gerações (ou seja, todos os objetos no heap gerenciado).

### <a name="survival-and-promotions"></a>Sobrevivência e promoções

Objects that are not reclaimed in a garbage collection are known as survivors and are promoted to the next generation. Objetos que sobrevivem a uma coleta de lixo da geração 0 são promovidos à geração 1; objetos que sobrevivem a uma coleta de lixo da geração 1 são promovidos à geração 2 e objetos que sobrevivem a uma coleta de lixo da geração 2 permanecem na geração 2.

When the garbage collector detects that the survival rate is high in a generation, it increases the threshold of allocations for that generation. The next collection gets a substantial size of reclaimed memory. The CLR continually balances two priorities: not letting an application's working set get too large by delaying garbage collection and not letting the garbage collection run too frequently.

### <a name="ephemeral-generations-and-segments"></a>Gerações e segmentos efêmeros

Devido ao fato de os objetos em gerações 0 e 1 serem de vida útil curta, essas gerações são conhecidas como as gerações efêmeras.

As gerações efêmeras devem ser alocadas no segmento de memória que é conhecido como o segmento efêmero. Cada novo segmento adquirido pelo coletor de lixo torna-se o novo segmento efêmero e contém os objetos que sobreviveram a uma coleta de lixo da geração 0. O segmento efêmero antigo torna-se o novo segmento da geração 2.

The size of the ephemeral segment varies depending on whether a system is 32-bit or 64-bit, and on the type of garbage collector it is running. Os valores padrão são mostrados na tabela a seguir.

||32 bits|64 bits|
|-|-------------|-------------|
|GC da estação de trabalho|16 MB|256 MB|
|GC do servidor|64 MB|4 GB|
|GC do Servidor com > 4 CPUs lógicas|32 MB|2 GB|
|GC do Servidor com > 8 CPUs lógicas|16 MB|1 GB|

O segmento efêmero pode incluir objetos da geração 2. Objetos da geração 2 podem usar vários segmentos (tantos quanto exigido pelo seu processo e permitido pela memória).

A quantidade de memória liberada de uma coleta de lixo efêmera é limitada ao tamanho do segmento efêmero. A quantidade de memória liberada é proporcional ao espaço que era ocupado pelos objetos inativos.

## <a name="what-happens-during-a-garbage-collection"></a>O que ocorre durante uma coleta de lixo

Uma coleta de lixo tem as seguintes fases:

- Uma fase de marcação que localiza todos os objetos vivos e cria uma lista desses objetos.

- Uma fase de relocação que atualiza as referências aos objetos que serão compactados.

- Uma fase de compactação que recupera o espaço ocupado por objetos inativos e compacta os objetos sobreviventes. A fase de compactação move objetos que sobreviveram a uma coleta de lixo em direção à extremidade mais antiga do segmento.

  Em virtude das coletas da geração 2 poderem ocupar vários segmentos, objetos que são promovidos para a geração 2 podem ser movidos para um segmento mais antigo. Tanto os sobreviventes da geração 1 quanto da geração 2 podem ser movidos para um segmento diferente, porque eles são promovidos para a geração 2.

  Ordinarily, the large object heap (LOH) is not compacted, because copying large objects imposes a performance penalty. However, in .NET Core and in .NET Framework 4.5.1 and later, you can use the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property to compact the large object heap on demand. In addition, the LOH is automatically compacted when a hard limit is set by specifying either:

  - a memory limit on a container, or
  - the [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) or [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) run-time configuration options

O coletor de lixo usa as informações a seguir para determinar se os objetos estão vivos:

- **Raízes de pilha**. Variáveis de pilha fornecidas pelo compilador JIT (just-in-time) e movimentador de pilhas. JIT optimizations can lengthen or shorten regions of code within which stack variables are reported to the garbage collector.

- **Identificadores de coleta de lixo**. Identificadores que apontam para objetos gerenciados e que podem ser alocados pelo código do usuário ou pelo Common Language Runtime.

- **Dados estáticos**. Objetos estáticos em domínios de aplicativo que podem fazer referência a outros objetos. Cada domínio de aplicativo controla seus objetos estáticos.

Antes de iniciar uma coleta de lixo, todos os threads gerenciados são suspensos, exceto o thread que disparou a coleta de lixo.

A ilustração a seguir mostra um thread que dispara uma coleta de lixo e faz com que outros threads sejam suspensos.

![When a thread triggers a Garbage Collection](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipulate unmanaged resources

If managed objects reference unmanaged objects by using their native file handles, you have to explicitly free the unmanaged objects, because the garbage collector only tracks memory on the managed heap.

Users of the managed object may not dispose the native resources used by the object. To perform the cleanup, you can make the managed object finalizable. Finalization consists of cleanup actions that execute when the object is no longer in use. When the managed object dies, it performs cleanup actions that are specified in its finalizer method.

Quando é descoberto que um objeto finalizável está inativo, seu finalizador é colocado em uma fila para que suas ações de limpeza sejam executadas, mas o próprio objeto é promovido para a próxima geração. Portanto, você precisa esperar até a próxima coleta de lixo ocorrer nessa geração (que não é necessariamente a próxima coleta de lixo) para determinar se o objeto foi recuperado.

For more information about finalization, see <xref:System.Object.Finalize?displayProperty=nameWithType>.

## <a name="workstation-and-server-garbage-collection"></a>Coleta de lixo de estação de trabalho ou de servidor

O coletor de lixo tem autoajuste e pode trabalhar em uma ampla variedade de cenários. You can use a [configuration file setting](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) to set the type of garbage collection based on the characteristics of the workload. O CLR fornece os seguintes tipos de coleta de lixo:

- Workstation garbage collection (GC) is designed for client apps. It is the default GC flavor for standalone apps. For hosted apps, for example, those hosted by ASP.NET, the host determines the default GC flavor.

  A coleta de lixo da estação de trabalho pode ser simultânea ou não simultânea. A coleta de lixo simultânea permite que os threads gerenciados continuem as operações durante uma coleta de lixo. [Background garbage collection](#background-workstation-garbage-collection) replaces [concurrent garbage collection](#concurrent-garbage-collection) in .NET Framework 4 and later versions.

- A coleta de lixo de servidor, que serve para aplicativos de servidor que precisam de escalabilidade e taxa de transferência altas.

  - In .NET Core, server garbage collection can be non-concurrent or background.

  - In .NET Framework 4.5 and later versions, server garbage collection can be non-concurrent or background (background garbage collection replaces concurrent garbage collection). In .NET Framework 4 and previous versions, server garbage collection is non-concurrent.

The following illustration shows the dedicated threads that perform the garbage collection on a server:

![Server Garbage Collection Threads](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Compare workstation and server garbage collection

Veja a seguir considerações de desempenho e de threading para a coleta de lixo da estação de trabalho:

- A coleção ocorre no thread do usuário que disparou a coleta de lixo e permanece com a mesma prioridade. Como os threads de usuário normalmente são executados com prioridade normal, o coletor de lixo (que é executado em um thread de prioridade normal) deve disputam competir outros threads por tempo da CPU. (Threads that run native code are not suspended on either server or workstation garbage collection.)

- Workstation garbage collection is always used on a computer that has only one processor, regardless of the [configuration setting](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

Veja a seguir considerações de desempenho e de threading para a coleta de lixo de servidor:

- A coleta ocorre em vários threads dedicados que estão em execução no nível de prioridade `THREAD_PRIORITY_HIGHEST`.

- Fornece-se um heap e um thread dedicado para executar a coleta de lixo para cada CPU, e os heaps são coletados ao mesmo tempo. Cada heap contém um heap de objeto pequeno e um heap de objeto grande, e todos os heaps podem ser acessados pelo código do usuário. Objetos em heaps diferentes podem fazer referência entre si.

- Como vários threads de coleta de lixo funcionam em conjunto, a coleta de lixo de servidor é mais rápida do que a coleta de lixo de estação de trabalho no heap de mesmo tamanho.

- Geralmente, a coleta de lixo de servidor tem segmentos maiores. However, this is only a generalization: segment size is implementation-specific and is subject to change. Don't make assumptions about the size of segments allocated by the garbage collector when tuning your app.

- A coleta de lixo de servidor pode usar bastante recursos. For example, imagine that there are 12 processes that use server GC running on a computer that has 4 processors. If all the processes happen to collect garbage at the same time, they would interfere with each other, as there would be 12 threads scheduled on the same processor. If the processes are active, it's not a good idea to have them all use server GC.

If you're running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled. Isso resultará na redução da comutação de contexto, o que pode melhorar o desempenho.

## <a name="background-workstation-garbage-collection"></a>Coleta de lixo de estação de trabalho em segundo plano

In background workstation garbage collection, ephemeral generations (0 and 1) are collected as needed while the collection of generation 2 is in progress. Background workstation garbage collection is performed on a dedicated thread and applies only to generation 2 collections.

Background garbage collection is enabled by default and can be enabled or disabled with the [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration setting in .NET Framework apps or the [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) setting in .NET Core apps.

> [!NOTE]
> Background garbage collection replaces [concurrent garbage collection](#concurrent-garbage-collection) and is available in .NET Framework 4 and later versions. In .NET Framework 4, it's supported only for workstation garbage collection. Starting with .NET Framework 4.5, background garbage collection is available for both workstation and server garbage collection.

Uma coleta em gerações efêmeras durante a coleta de lixo em segundo plano é conhecida como coleta de lixo em primeiro plano. Quando as coletas de lixo em primeiro plano ocorrem, todos os threads gerenciados são suspensos.

When background garbage collection is in progress and you've allocated enough objects in generation 0, the CLR performs a generation 0 or generation 1 foreground garbage collection. O thread dedicado de coleta de lixo em segundo plano verifica em pontos frequentes de segurança se há uma solicitação de coleta de lixo em primeiro plano. Se houver, a coleta de plano de fundo suspende a si mesma para que a coleta de lixo em primeiro plano possa ocorrer. Após a coleta de lixo em primeiro plano, o thread dedicado de coleta de lixo em segundo plano e os threads de usuário continuam.

A coleta de lixo em segundo plano remove as restrições de alocação impostas pela coleta de lixo simultânea, pois as coletas de lixo efêmeras podem ocorrer durante a coleta de lixo em segundo plano. Background garbage collection can remove dead objects in ephemeral generations. It can also expand the heap if needed during a generation 1 garbage collection.

A ilustração a seguir mostra a coleta de lixo em segundo plano executada em um thread dedicado separado em uma estação de trabalho:

![Coleta de lixo de estação de trabalho em segundo plano](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Coleta de lixo de servidor em segundo plano

Starting with .NET Framework 4.5, background server garbage collection is the default mode for server garbage collection.

Background server garbage collection functions similarly to background workstation garbage collection, described in the previous section, but there are a few differences:

- Background workstation garbage collection uses one dedicated background garbage collection thread, whereas background server garbage collection uses multiple threads. Typically, there's a dedicated thread for each logical processor.

- Ao contrário do thread de coleta de lixo de estação de trabalho em segundo plano, esses threads não têm tempo limite.

A ilustração a seguir mostra a coleta de lixo em segundo plano executada em um thread dedicado separado em um servidor:

![Coleta de lixo de servidor em segundo plano](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Coleta de lixo simultânea

> [!TIP]
> This section applies to:
>
> - .NET Framework 3.5 and earlier for workstation garbage collection
> - .NET Framework 4 and earlier for server garbage collection
>
> Concurrent garbage is replaced by [background garbage collection](#background-workstation-garbage-collection) in later versions.

In workstation or server garbage collection, you can [enable concurrent garbage collection](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), which enables threads to run concurrently with a dedicated thread that performs the garbage collection for most of the duration of the collection. Essa opção afeta apenas as coletas de lixo na geração 2. As gerações 0 e 1 são sempre não simultâneas, pois terminarem muito rápido.

A coleta de lixo simultânea permite que aplicativos interativos sejam mais responsivos minimizando a pausa para uma coleta. Na maioria das vezes, a execução dos threads gerenciados pode continuar enquanto o thread de coleta de lixo simultânea estiver em execução. Isso resulta em pausas menores enquanto uma coleta de lixo estiver em execução.

A coleta de lixo simultânea é executada em um thread dedicado. Por padrão, o CLR executa a coleta de lixo de estação de trabalho com a coleta de lixo simultânea habilitada. Isso é verdadeiro para computadores com processador único e vários processadores.

A ilustração a seguir mostra a coleta de lixo simultânea executada em um thread dedicado separado.

![Concurrent Garbage Collection Threads](./media/gc-concurrent.png)

## <a name="see-also"></a>Consulte também

- [Configuration options for GC](../../core/run-time-config/garbage-collector.md)
- [Coleta de lixo](index.md)
