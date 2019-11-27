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

No Common Language Runtime (CLR), o coletor de lixo (GC) serve como um Gerenciador de memória automático. Ele oferece os seguintes benefícios:

- Permite que você desenvolva seu aplicativo sem precisar liberar memória manualmente.

- Aloca objetos no heap gerenciado com eficiência.

- Recupera os objetos que não estão sendo usados, limpa a memória e mantém a memória disponível para alocações futuras. Os objetos gerenciados obtêm automaticamente conteúdo limpo com o qual começar, portanto, seus construtores não precisam inicializar cada campo de dados.

- Fornece segurança de memória, assegurando que um objeto não possa usar o conteúdo de outro objeto.

Este artigo descreve os principais conceitos da coleta de lixo.

## <a name="fundamentals-of-memory"></a>Conceitos básicos de memória

A lista a seguir resume conceitos importantes de memória do CLR.

- Cada processo tem seu próprio espaço de endereço virtual separado. Todos os processos no mesmo computador compartilham a mesma memória física e o arquivo de paginação, se houver um.

- Por padrão, em computadores de 32 bits, cada processo tem um espaço de endereço virtual no modo de usuário de 2 GB.

- Como desenvolvedor de aplicativos, você trabalha apenas com o espaço de endereço virtual e nunca manipula a memória física diretamente. O coletor de lixo aloca e libera memória virtual para você no heap gerenciado.

  Se você estiver escrevendo código nativo, use as funções do Windows para trabalhar com o espaço de endereço virtual. Essas funções alocam e liberam memória virtual para você em heaps nativos.

- A memória virtual pode estar em três estados:

  - Livre. O bloco de memória não tem referências a ele e está disponível para alocação.

  - Reservado. O bloco de memória está disponível para seu uso e não pode ser usado para nenhuma outra solicitação de alocação. No entanto, você não pode armazenar dados nesse bloco de memória até que ele esteja comprometido.

  - Comprometido. O bloco de memória é atribuído para armazenamento físico.

- O espaço de endereço virtual pode ficar fragmentado. Isso significa que há blocos livres, também conhecido como furos, no espaço de endereço. Quando uma alocação de memória virtual é solicitada, o gerenciador de memória virtual precisa localizar um único bloco livre suficientemente grande para atender a essa solicitação de alocação. Mesmo que você tenha 2 GB de espaço livre, a alocação que exige 2 GB não será bem-sucedida a menos que todo esse espaço livre esteja em um único bloco de endereço.

- Você pode ficar sem memória se não houver espaço de endereço virtual suficiente para reservar ou espaço físico para confirmar.

  O arquivo de paginação é usado mesmo se a pressão de memória física (ou seja, a demanda de memória física) estiver baixa. Na primeira vez que a pressão de memória física é alta, o sistema operacional deve liberar espaço na memória física para armazenar dados e faz backup de alguns dos dados que estão na memória física para o arquivo de paginação. Esses dados não são paginados até que seja necessário, portanto, é possível encontrar paginação em situações em que a pressão da memória física está baixa.

## <a name="conditions-for-a-garbage-collection"></a>Condições para uma coleta de lixo

A coleta de lixo ocorre quando uma das seguintes condições é verdadeira:

- O sistema tem pouca memória física. Isso é detectado pela notificação de memória insuficiente do sistema operacional ou memória insuficiente, conforme indicado pelo host.

- A memória usada por objetos alocados no heap gerenciado ultrapassa o limite aceitável. Esse limite é ajustado continuamente enquanto o processo é executado.

- O método <xref:System.GC.Collect%2A?displayProperty=nameWithType> é chamado. Em quase todos os casos, você não precisa chamar esse método porque o coletor de lixo funciona continuamente. Esse método é usado principalmente para situações exclusivas e testes.

## <a name="the-managed-heap"></a>O heap gerenciado

Depois que o coletor de lixo é inicializado pelo CLR, ele aloca um segmento da memória para armazenar e gerenciar objetos. Essa memória é chamada de heap gerenciado, em contraposição a um heap nativo no sistema operacional.

Há um heap gerenciado para cada processo gerenciado. Todos os threads no processo alocam memória para objetos no mesmo heap.

Para reservar memória, o coletor de lixo chama a função do Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) e reserva um segmento de memória por vez para aplicativos gerenciados. O coletor de lixo também reserva segmentos, conforme necessário, e libera segmentos de volta para o sistema operacional (depois de limpá-los de qualquer objeto) chamando a função [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) do Windows.

> [!IMPORTANT]
> O tamanho de segmentos alocados pelo coletor de lixo é específico da implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas. Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.

Quanto menos objetos alocados no heap, menos trabalho o coletor de lixo precisa fazer. Ao alocar objetos, não use valores arredondados que excedam suas necessidades, por exemplo, alocando uma matriz de 32 bytes quando são necessários apenas 15 bytes.

Quando uma coleta de lixo é disparada, o coletor de lixo recupera a memória ocupada por objetos inativos. O processo de recuperação compacta objetos vivos para que eles sejam movidos juntos e o espaço inativo é removido, tornando o heap menor. Isso garante que os objetos que são alocados juntos permaneçam juntos no heap gerenciado, para preservar sua localidade.

O grau de intrusão (frequência e a duração) de coletas de lixo é o resultado do volume de alocações e da quantidade de memória restante no heap gerenciado.

O heap pode ser considerado como o acúmulo de dois heaps: o [heap de objetos grandes](large-object-heap.md) e o heap de objetos pequenos.

O [heap de objetos grandes](large-object-heap.md) contém objetos muito grandes, com 85.000 bytes ou mais. Os objetos no heap de objetos grandes normalmente são matrizes. É raro que um objeto de instância seja muito grande.

> [!TIP]
> Você pode [Configurar o tamanho do limite](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) para objetos a serem acessados no heap de objeto grande.

## <a name="generations"></a>Gerações

O heap está organizado em gerações de modo que possa manipular objetos de vida útil longa e curta. A coleta de lixo ocorre principalmente com a recuperação de objetos de vida útil curta, que geralmente ocupam apenas uma pequena parte do heap. Há três gerações de objetos no heap:

- **Geração 0**. Essa é a geração mais jovem e contém objetos de vida útil curta. Um exemplo de um objeto de vida útil curta é uma variável temporária. A coleta de lixo ocorre com mais frequência nessa geração.

  Os objetos alocados recentemente formam uma nova geração de objetos e são coleções de 0 geração implicitamente. No entanto, se forem objetos grandes, eles irão para o heap de objeto grande em uma coleção de geração 2.

  A maioria dos objetos são recuperados para coleta de lixo na geração 0 e não sobrevivem para a próxima geração.

- **Geração 1**. Essa geração contém objetos de vida útil curta e serve como um buffer entre objetos de vida útil curta e longa.

- **Geração 2**. Essa geração contém objetos de vida útil longa. Um exemplo de um objeto de vida longa é um objeto em um aplicativo de servidor que contém dados estáticos que residem durante o processo.

Coletas de lixo ocorrem em gerações específicas conforme as condições permitirem. Coletar uma geração significa coletar objetos nessa geração e todas as suas gerações mais jovens. Uma coleta de lixo da geração 2 também é conhecida como uma coleta de lixo completa, pois ela recupera todos os objetos em todas as gerações (ou seja, todos os objetos no heap gerenciado).

### <a name="survival-and-promotions"></a>Sobrevivência e promoções

Os objetos que não são recuperados em uma coleta de lixo são conhecidos como os sobreviventes e são promovidos para a próxima geração. Objetos que sobrevivem a uma coleta de lixo da geração 0 são promovidos à geração 1; objetos que sobrevivem a uma coleta de lixo da geração 1 são promovidos à geração 2 e objetos que sobrevivem a uma coleta de lixo da geração 2 permanecem na geração 2.

Quando o coletor de lixo detecta que a taxa de sobrevivência é alta em uma geração, ela aumenta o limite de alocações para essa geração. A próxima coleção Obtém um tamanho substancial de memória recuperada. O CLR balanceia continuamente duas prioridades: não permitir que o conjunto de trabalho de um aplicativo fique muito grande atrasando a coleta de lixo e não permitindo que a coleta de lixo seja executada com muita frequência.

### <a name="ephemeral-generations-and-segments"></a>Gerações e segmentos efêmeros

Devido ao fato de os objetos em gerações 0 e 1 serem de vida útil curta, essas gerações são conhecidas como as gerações efêmeras.

As gerações efêmeras devem ser alocadas no segmento de memória que é conhecido como o segmento efêmero. Cada novo segmento adquirido pelo coletor de lixo torna-se o novo segmento efêmero e contém os objetos que sobreviveram a uma coleta de lixo da geração 0. O segmento efêmero antigo torna-se o novo segmento da geração 2.

O tamanho do segmento efêmero varia dependendo se um sistema for de 32 bits ou de 64 bits e sobre o tipo de coletor de lixo em execução. Os valores padrão são mostrados na tabela a seguir.

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

  Normalmente, o LOH (heap de objeto grande) não é compactado, pois copiar objetos grandes impõe uma penalidade de desempenho. No entanto, no .NET Core e no .NET Framework 4.5.1 e posterior, você pode usar a propriedade <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> para compactar o heap de objeto grande sob demanda. Além disso, o LOH é compactado automaticamente quando um limite rígido é definido especificando:

  - um limite de memória em um contêiner ou
  - as opções de configuração de tempo de execução do [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) ou [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)

O coletor de lixo usa as informações a seguir para determinar se os objetos estão vivos:

- **Raízes de pilha**. Variáveis de pilha fornecidas pelo compilador JIT (just-in-time) e movimentador de pilhas. As otimizações JIT podem aumentar ou diminuir as regiões do código dentro das quais as variáveis de pilha são relatadas ao coletor de lixo.

- **Identificadores de coleta de lixo**. Identificadores que apontam para objetos gerenciados e que podem ser alocados pelo código do usuário ou pelo Common Language Runtime.

- **Dados estáticos**. Objetos estáticos em domínios de aplicativo que podem fazer referência a outros objetos. Cada domínio de aplicativo controla seus objetos estáticos.

Antes de iniciar uma coleta de lixo, todos os threads gerenciados são suspensos, exceto o thread que disparou a coleta de lixo.

A ilustração a seguir mostra um thread que dispara uma coleta de lixo e faz com que outros threads sejam suspensos.

![Quando um thread dispara uma coleta de lixo](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipular recursos não gerenciados

Se os objetos gerenciados fizerem referência a objetos não gerenciados usando seus identificadores de arquivo nativos, você terá que liberar explicitamente os objetos não gerenciados, pois o coletor de lixo rastreia apenas a memória no heap gerenciado.

Os usuários do objeto gerenciado podem não descartar os recursos nativos usados pelo objeto. Para executar a limpeza, você pode tornar o objeto gerenciado finalizável. A finalização consiste em ações de limpeza que são executadas quando o objeto não está mais em uso. Quando o objeto gerenciado é desativado, ele executa ações de limpeza que são especificadas em seu método de finalizador.

Quando é descoberto que um objeto finalizável está inativo, seu finalizador é colocado em uma fila para que suas ações de limpeza sejam executadas, mas o próprio objeto é promovido para a próxima geração. Portanto, você precisa esperar até a próxima coleta de lixo ocorrer nessa geração (que não é necessariamente a próxima coleta de lixo) para determinar se o objeto foi recuperado.

Para obter mais informações sobre finalização, consulte <xref:System.Object.Finalize?displayProperty=nameWithType>.

## <a name="workstation-and-server-garbage-collection"></a>Coleta de lixo de estação de trabalho ou de servidor

O coletor de lixo tem autoajuste e pode trabalhar em uma ampla variedade de cenários. Você pode usar uma [configuração de arquivo de configuração](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) para definir o tipo de coleta de lixo com base nas características da carga de trabalho. O CLR fornece os seguintes tipos de coleta de lixo:

- A coleta de lixo de estação de trabalho (GC) foi projetada para aplicativos cliente. É o tipo de GC padrão para aplicativos autônomos. Para aplicativos hospedados, por exemplo, aqueles hospedados por ASP.NET, o host determina o tipo GC padrão.

  A coleta de lixo da estação de trabalho pode ser simultânea ou não simultânea. A coleta de lixo simultânea permite que os threads gerenciados continuem as operações durante uma coleta de lixo. A [coleta de lixo em segundo plano](#background-workstation-garbage-collection) substitui a [coleta de lixo simultânea](#concurrent-garbage-collection) no .NET Framework 4 e versões posteriores.

- A coleta de lixo de servidor, que serve para aplicativos de servidor que precisam de escalabilidade e taxa de transferência altas.

  - No .NET Core, a coleta de lixo do servidor pode ser não simultânea ou em segundo plano.

  - No .NET Framework 4,5 e versões posteriores, a coleta de lixo do servidor pode ser não simultânea ou em segundo plano (a coleta de lixo em segundo plano substitui a coleta de lixo simultânea). No .NET Framework 4 e versões anteriores, a coleta de lixo do servidor é não simultânea.

A ilustração a seguir mostra os threads dedicados que executam a coleta de lixo em um servidor:

![Threads de coleta de lixo do servidor](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Comparar a coleta de lixo da estação de trabalho e do servidor

Veja a seguir considerações de desempenho e de threading para a coleta de lixo da estação de trabalho:

- A coleção ocorre no thread do usuário que disparou a coleta de lixo e permanece com a mesma prioridade. Como os threads de usuário normalmente são executados com prioridade normal, o coletor de lixo (que é executado em um thread de prioridade normal) deve disputam competir outros threads por tempo da CPU. (Os threads que executam código nativo não são suspensos na coleta de lixo do servidor ou da estação de trabalho.)

- A coleta de lixo de estação de trabalho é sempre usada em um computador que tem apenas um processador, independentemente da [definição de configuração](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

Veja a seguir considerações de desempenho e de threading para a coleta de lixo de servidor:

- A coleta ocorre em vários threads dedicados que estão em execução no nível de prioridade `THREAD_PRIORITY_HIGHEST`.

- Fornece-se um heap e um thread dedicado para executar a coleta de lixo para cada CPU, e os heaps são coletados ao mesmo tempo. Cada heap contém um heap de objeto pequeno e um heap de objeto grande, e todos os heaps podem ser acessados pelo código do usuário. Objetos em heaps diferentes podem fazer referência entre si.

- Como vários threads de coleta de lixo funcionam em conjunto, a coleta de lixo de servidor é mais rápida do que a coleta de lixo de estação de trabalho no heap de mesmo tamanho.

- Geralmente, a coleta de lixo de servidor tem segmentos maiores. No entanto, essa é apenas uma generalização: o tamanho do segmento é específico da implementação e está sujeito a alterações. Não faça suposições sobre o tamanho dos segmentos alocados pelo coletor de lixo ao ajustar seu aplicativo.

- A coleta de lixo de servidor pode usar bastante recursos. Por exemplo, imagine que haja 12 processos que usam GC de servidor em execução em um computador com 4 processadores. Se todos os processos ocorrerem para coletar lixo ao mesmo tempo, eles interferirão uns com os outros, pois haveria 12 threads agendados no mesmo processador. Se os processos estiverem ativos, não é uma boa ideia fazer com que todos usem o GC do servidor.

Se você estiver executando centenas de instâncias de um aplicativo, considere usar a coleta de lixo da estação de trabalho com a coleta de lixo simultânea desabilitada. Isso resultará na redução da comutação de contexto, o que pode melhorar o desempenho.

## <a name="background-workstation-garbage-collection"></a>Coleta de lixo de estação de trabalho em segundo plano

Na coleta de lixo da estação de trabalho em segundo plano, as gerações efêmeras (0 e 1) são coletadas conforme necessário enquanto a coleta da geração 2 está em andamento. A coleta de lixo da estação de trabalho em segundo plano é executada em um thread dedicado e aplica-se somente às coleções da geração 2.

A coleta de lixo em segundo plano é habilitada por padrão e pode ser habilitada ou desabilitada com a definição de configuração [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) em aplicativos .NET Framework ou a configuração [System. GC. simultânea](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) em aplicativos .NET Core.

> [!NOTE]
> A coleta de lixo em segundo plano substitui a [coleta de lixo simultânea](#concurrent-garbage-collection) e está disponível no .NET Framework 4 e em versões posteriores. No .NET Framework 4, há suporte apenas para coleta de lixo de estação de trabalho. A partir do .NET Framework 4,5, a coleta de lixo em segundo plano está disponível para a coleta de lixo da estação de trabalho e do servidor.

Uma coleta em gerações efêmeras durante a coleta de lixo em segundo plano é conhecida como coleta de lixo em primeiro plano. Quando as coletas de lixo em primeiro plano ocorrem, todos os threads gerenciados são suspensos.

Quando a coleta de lixo em segundo plano estiver em andamento e você tiver alocado objetos suficientes na geração 0, o CLR executará uma coleta de lixo de primeiro plano de geração 0 ou geração 1. O thread dedicado de coleta de lixo em segundo plano verifica em pontos frequentes de segurança se há uma solicitação de coleta de lixo em primeiro plano. Se houver, a coleta de plano de fundo suspende a si mesma para que a coleta de lixo em primeiro plano possa ocorrer. Após a coleta de lixo em primeiro plano, o thread dedicado de coleta de lixo em segundo plano e os threads de usuário continuam.

A coleta de lixo em segundo plano remove as restrições de alocação impostas pela coleta de lixo simultânea, pois as coletas de lixo efêmeras podem ocorrer durante a coleta de lixo em segundo plano. A coleta de lixo em segundo plano pode remover objetos inativos em gerações efêmeras. Ele também pode expandir o heap, se necessário, durante uma coleta de lixo de geração 1.

A ilustração a seguir mostra a coleta de lixo em segundo plano executada em um thread dedicado separado em uma estação de trabalho:

![Coleta de lixo de estação de trabalho em segundo plano](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Coleta de lixo de servidor em segundo plano

A partir do .NET Framework 4,5, a coleta de lixo do servidor em segundo plano é o modo padrão para a coleta de lixo do servidor.

A coleta de lixo do servidor em segundo plano funciona de forma semelhante à coleta de lixo da estação de trabalho em segundo plano, descrita na seção anterior, mas há algumas diferenças:

- A coleta de lixo da estação de trabalho em segundo plano usa um thread de coleta de lixo de segundo plano dedicado, enquanto a coleta de lixo do servidor de segundo Normalmente, há um thread dedicado para cada processador lógico.

- Ao contrário do thread de coleta de lixo de estação de trabalho em segundo plano, esses threads não têm tempo limite.

A ilustração a seguir mostra a coleta de lixo em segundo plano executada em um thread dedicado separado em um servidor:

![Coleta de lixo de servidor em segundo plano](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Coleta de lixo simultânea

> [!TIP]
> Esta seção aplica-se a:
>
> - .NET Framework 3,5 e anteriores para coleta de lixo de estação de trabalho
> - .NET Framework 4 e anterior para coleta de lixo do servidor
>
> O lixo simultâneo é substituído pela [coleta de lixo em segundo plano](#background-workstation-garbage-collection) em versões posteriores.

Na coleta de lixo da estação de trabalho ou do servidor, você pode [habilitar a coleta de lixo simultânea](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), o que permite que os threads sejam executados simultaneamente com um thread dedicado que executa a coleta de lixo para a maior parte da duração da coleção. Essa opção afeta apenas as coletas de lixo na geração 2. As gerações 0 e 1 são sempre não simultâneas, pois terminarem muito rápido.

A coleta de lixo simultânea permite que aplicativos interativos sejam mais responsivos minimizando a pausa para uma coleta. Na maioria das vezes, a execução dos threads gerenciados pode continuar enquanto o thread de coleta de lixo simultânea estiver em execução. Isso resulta em pausas menores enquanto uma coleta de lixo estiver em execução.

A coleta de lixo simultânea é executada em um thread dedicado. Por padrão, o CLR executa a coleta de lixo de estação de trabalho com a coleta de lixo simultânea habilitada. Isso é verdadeiro para computadores com processador único e vários processadores.

A ilustração a seguir mostra a coleta de lixo simultânea executada em um thread dedicado separado.

![Threads de coleta de lixo simultâneos](./media/gc-concurrent.png)

## <a name="see-also"></a>Consulte também

- [Opções de configuração para GC](../../core/run-time-config/garbage-collector.md)
- [Coleta de lixo](index.md)
