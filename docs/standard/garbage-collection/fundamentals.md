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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400536"
---
# <a name="fundamentals-of-garbage-collection"></a>Noções básicas da coleta de lixo

No tempo de execução da linguagem comum (CLR), o coletor de lixo (GC) serve como um gerenciador automático de memória. Ele oferece os seguintes benefícios:

- Permite que você desenvolva seu aplicativo sem ter que liberar manualmente a memória.

- Aloca objetos no heap gerenciado com eficiência.

- Recupera os objetos que não estão sendo usados, limpa a memória e mantém a memória disponível para alocações futuras. Os objetos gerenciados obtêm automaticamente conteúdo limpo com o qual começar, portanto, seus construtores não precisam inicializar cada campo de dados.

- Fornece segurança de memória, assegurando que um objeto não possa usar o conteúdo de outro objeto.

Este artigo descreve os conceitos centrais da coleta de lixo.

## <a name="fundamentals-of-memory"></a>Conceitos básicos de memória

A lista a seguir resume conceitos importantes de memória do CLR.

- Cada processo tem seu próprio espaço de endereço virtual separado. Todos os processos no mesmo computador compartilham a mesma memória física e o arquivo de página, se houver um.

- Por padrão, em computadores de 32 bits, cada processo tem um espaço de endereço virtual no modo de usuário de 2 GB.

- Como desenvolvedor de aplicativos, você trabalha apenas com o espaço de endereço virtual e nunca manipula a memória física diretamente. O coletor de lixo aloca e libera memória virtual para você no heap gerenciado.

  Se você estiver escrevendo código nativo, você usa funções do Windows para trabalhar com o espaço de endereço virtual. Essas funções alocam e liberam memória virtual para você em heaps nativos.

- A memória virtual pode estar em três estados:

  - Livre. O bloco de memória não tem referências a ele e está disponível para alocação.

  - Reservado. O bloco de memória está disponível para seu uso e não pode ser usado para nenhuma outra solicitação de alocação. No entanto, você não pode armazenar dados nesse bloco de memória até que ele esteja comprometido.

  - Comprometido. O bloco de memória é atribuído para armazenamento físico.

- O espaço de endereço virtual pode ficar fragmentado. Isso significa que há blocos livres, também conhecido como furos, no espaço de endereço. Quando uma alocação de memória virtual é solicitada, o gerenciador de memória virtual precisa localizar um único bloco livre suficientemente grande para atender a essa solicitação de alocação. Mesmo que você tenha 2 GB de espaço livre, a alocação que exige 2 GB não será bem-sucedida a menos que todo esse espaço livre esteja em um único bloco de endereço.

- Você pode ficar sem memória se não houver espaço de endereço virtual suficiente para reservar ou espaço físico para se comprometer.

  O arquivo de página é usado mesmo que a pressão de memória física (ou seja, a demanda por memória física) seja baixa. A primeira vez que a pressão da memória física é alta, o sistema operacional deve abrir espaço na memória física para armazenar dados, e faz backup de alguns dos dados que estão na memória física para o arquivo da página. Esses dados não são paginados até que sejam necessários, então é possível encontrar paginação em situações onde a pressão da memória física é baixa.

## <a name="conditions-for-a-garbage-collection"></a>Condições para uma coleta de lixo

A coleta de lixo ocorre quando uma das seguintes condições é verdadeira:

- O sistema tem pouca memória física. Isso é detectado pela notificação de memória baixa do SISTEMA OPERACIONAL ou pela memória baixa, conforme indicado pelo host.

- A memória usada por objetos alocados no heap gerenciado ultrapassa o limite aceitável. Esse limite é ajustado continuamente enquanto o processo é executado.

- O método <xref:System.GC.Collect%2A?displayProperty=nameWithType> é chamado. Em quase todos os casos, você não precisa chamar esse método porque o coletor de lixo funciona continuamente. Esse método é usado principalmente para situações exclusivas e testes.

## <a name="the-managed-heap"></a>O heap gerenciado

Depois que o coletor de lixo é inicializado pelo CLR, ele aloca um segmento da memória para armazenar e gerenciar objetos. Essa memória é chamada de heap gerenciado, em contraposição a um heap nativo no sistema operacional.

Há um heap gerenciado para cada processo gerenciado. Todos os threads no processo alocam memória para objetos no mesmo heap.

Para reservar memória, o coletor de lixo chama a função Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) e reserva um segmento de memória por vez para aplicativos gerenciados. O coletor de lixo também reserva segmentos, conforme necessário, e libera segmentos de volta ao sistema operacional (depois de limpá-los de quaisquer objetos) chamando a função [Windows VirtualFree.](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)

> [!IMPORTANT]
> O tamanho de segmentos alocados pelo coletor de lixo é específico da implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas. Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.

Quanto menos objetos alocados no heap, menos trabalho o coletor de lixo precisa fazer. Ao alocar objetos, não use valores arredondados que excedam suas necessidades, por exemplo, alocando uma matriz de 32 bytes quando são necessários apenas 15 bytes.

Quando uma coleta de lixo é disparada, o coletor de lixo recupera a memória ocupada por objetos inativos. O processo de recuperação compacta objetos vivos para que eles sejam movidos juntos e o espaço inativo é removido, tornando o heap menor. Isso garante que os objetos que são alocados juntos permaneçam juntos no heap gerenciado, para preservar sua localidade.

O grau de intrusão (frequência e a duração) de coletas de lixo é o resultado do volume de alocações e da quantidade de memória restante no heap gerenciado.

O heap pode ser considerado como o acúmulo de dois heaps: o [heap de objetos grandes](large-object-heap.md) e o heap de objetos pequenos.

O [heap de objetos grandes](large-object-heap.md) contém objetos muito grandes, com 85.000 bytes ou mais. Os objetos no heap de objetos grandes normalmente são matrizes. É raro que um objeto de instância seja muito grande.

> [!TIP]
> Você pode [configurar o tamanho do limiar](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) para os objetos irem no heap de objeto grande.

## <a name="generations"></a>Gerações

O heap está organizado em gerações de modo que possa manipular objetos de vida útil longa e curta. A coleta de lixo ocorre principalmente com a recuperação de objetos de vida útil curta, que geralmente ocupam apenas uma pequena parte do heap. Há três gerações de objetos no heap:

- **Geração 0**. Essa é a geração mais jovem e contém objetos de vida útil curta. Um exemplo de um objeto de vida útil curta é uma variável temporária. A coleta de lixo ocorre com mais frequência nessa geração.

  Objetos recém-alocados formam uma nova geração de objetos e são implicitamente coleções de geração 0. No entanto, se eles são objetos grandes, eles vão sobre o grande monte de objetos em uma coleção de geração 2.

  A maioria dos objetos são recuperados para coleta de lixo na geração 0 e não sobrevivem para a próxima geração.

- **Geração 1**. Essa geração contém objetos de vida útil curta e serve como um buffer entre objetos de vida útil curta e longa.

- **Geração 2**. Essa geração contém objetos de vida útil longa. Um exemplo de objeto de longa duração é um objeto em um aplicativo de servidor que contém dados estáticos que estão ativos durante a duração do processo.

Coletas de lixo ocorrem em gerações específicas conforme as condições permitirem. Coletar uma geração significa coletar objetos nessa geração e todas as suas gerações mais jovens. Uma coleta de lixo da geração 2 também é conhecida como uma coleta de lixo completa, pois ela recupera todos os objetos em todas as gerações (ou seja, todos os objetos no heap gerenciado).

### <a name="survival-and-promotions"></a>Sobrevivência e promoções

Objetos que não são recuperados em uma coleta de lixo são conhecidos como sobreviventes e são promovidos para a próxima geração. Objetos que sobrevivem a uma coleta de lixo da geração 0 são promovidos à geração 1; objetos que sobrevivem a uma coleta de lixo da geração 1 são promovidos à geração 2 e objetos que sobrevivem a uma coleta de lixo da geração 2 permanecem na geração 2.

Quando o coletor de lixo detecta que a taxa de sobrevivência é alta em uma geração, aumenta o limiar de alocações para essa geração. A próxima coleção recebe um tamanho substancial de memória recuperada. A CLR equilibra continuamente duas prioridades: não deixar o conjunto de trabalho de um aplicativo ficar muito grande, atrasando a coleta de lixo e não deixando a coleta de lixo correr com muita freqüência.

### <a name="ephemeral-generations-and-segments"></a>Gerações e segmentos efêmeros

Devido ao fato de os objetos em gerações 0 e 1 serem de vida útil curta, essas gerações são conhecidas como as gerações efêmeras.

As gerações efêmeras devem ser alocadas no segmento de memória que é conhecido como o segmento efêmero. Cada novo segmento adquirido pelo coletor de lixo torna-se o novo segmento efêmero e contém os objetos que sobreviveram a uma coleta de lixo da geração 0. O segmento efêmero antigo torna-se o novo segmento da geração 2.

O tamanho do segmento efêmero varia dependendo se um sistema é de 32 bits ou 64 bits, e sobre o tipo de coletor de lixo que está executando. Os valores padrão são mostrados na tabela a seguir.

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

  Normalmente, o heap de objeto grande (LOH) não é compactado, porque copiar objetos grandes impõe uma penalidade de desempenho. No entanto, no .NET Core e no .NET Framework 4.5.1 e posterior, você pode usar a <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> propriedade para compactar o grande monte de objetos demanda. Além disso, o LOH é automaticamente compactado quando um limite rígido é definido especificando:

  - um limite de memória em um recipiente, ou
  - as opções de [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) configuração de tempo de execução [GCHeapHardLimitLimitOu](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit)

O coletor de lixo usa as informações a seguir para determinar se os objetos estão vivos:

- **Empilhar raízes**. Variáveis de pilha fornecidas pelo compilador JIT (just-in-time) e movimentador de pilhas. As otimizações do JIT podem alongar ou encurtar regiões de código dentro das quais as variáveis de pilha são relatadas ao coletor de lixo.

- **Alças de coleta de lixo**. Identificadores que apontam para objetos gerenciados e que podem ser alocados pelo código do usuário ou pelo Common Language Runtime.

- **Dados estáticos**. Objetos estáticos em domínios de aplicativo que podem fazer referência a outros objetos. Cada domínio de aplicativo controla seus objetos estáticos.

Antes de iniciar uma coleta de lixo, todos os threads gerenciados são suspensos, exceto o thread que disparou a coleta de lixo.

A ilustração a seguir mostra um thread que dispara uma coleta de lixo e faz com que outros threads sejam suspensos.

![Quando um segmento aciona uma coleta de lixo](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipular recursos não gerenciados

Se objetos gerenciados referenciam objetos não gerenciados usando suas alças de arquivo nativas, você tem que liberar explicitamente os objetos não gerenciados, porque o coletor de lixo só rastreia a memória no heap gerenciado.

Os usuários do objeto gerenciado não podem descartar os recursos nativos usados pelo objeto. Para realizar a limpeza, você pode tornar o objeto gerenciado finalizado. A finalização consiste em ações de limpeza que são executadas quando o objeto não está mais em uso. Quando o objeto gerenciado morre, ele executa ações de limpeza especificadas em seu método finalizador.

Quando é descoberto que um objeto finalizável está inativo, seu finalizador é colocado em uma fila para que suas ações de limpeza sejam executadas, mas o próprio objeto é promovido para a próxima geração. Portanto, você precisa esperar até a próxima coleta de lixo ocorrer nessa geração (que não é necessariamente a próxima coleta de lixo) para determinar se o objeto foi recuperado.

Para obter mais informações <xref:System.Object.Finalize?displayProperty=nameWithType>sobre finalização, consulte .

## <a name="workstation-and-server-garbage-collection"></a>Coleta de lixo de estação de trabalho ou de servidor

O coletor de lixo tem autoajuste e pode trabalhar em uma ampla variedade de cenários. Você pode usar uma [configuração de arquivo](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) para definir o tipo de coleta de lixo com base nas características da carga de trabalho. O CLR fornece os seguintes tipos de coleta de lixo:

- A coleta de lixo da estação de trabalho (GC) é projetada para aplicativos de clientes. É o sabor GC padrão para aplicativos autônomos. Para aplicativos hospedados, por exemplo, aqueles hospedados por ASP.NET, o host determina o sabor GC padrão.

  A coleta de lixo da estação de trabalho pode ser simultânea ou não simultânea. A coleta de lixo simultânea permite que os threads gerenciados continuem as operações durante uma coleta de lixo. [A coleta de lixo em segundo plano](#background-workstation-garbage-collection) substitui a coleta de lixo [simultânea](#concurrent-garbage-collection) nas versões .NET Framework 4 e posteriores.

- A coleta de lixo de servidor, que serve para aplicativos de servidor que precisam de escalabilidade e taxa de transferência altas.

  - No .NET Core, a coleta de lixo do servidor pode ser não simultânea ou em segundo plano.

  - No Framework 4.5 e posteriores, a coleta de lixo do servidor pode ser não simultânea ou em segundo plano (a coleta de lixo em segundo plano substitui a coleta de lixo simultânea). No Framework 4 e nas versões anteriores, a coleta de lixo do servidor não é simultânea.

A ilustração a seguir mostra os tópicos dedicados que realizam a coleta de lixo em um servidor:

![Threads de coleta de lixo do servidor](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Compare a estação de trabalho e a coleta de lixo do servidor

Veja a seguir considerações de desempenho e de threading para a coleta de lixo da estação de trabalho:

- A coleção ocorre no thread do usuário que disparou a coleta de lixo e permanece com a mesma prioridade. Como os threads de usuário normalmente são executados com prioridade normal, o coletor de lixo (que é executado em um thread de prioridade normal) deve disputam competir outros threads por tempo da CPU. (Os threads que executam código nativo não estão suspensos em nenhuma coleta de lixo do servidor ou da estação de trabalho.)

- A coleta de lixo da estação de trabalho é sempre usada em um computador que tem apenas um processador, independentemente da [configuração de configuração](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

Veja a seguir considerações de desempenho e de threading para a coleta de lixo de servidor:

- A coleta ocorre em vários threads dedicados que estão em execução no nível de prioridade `THREAD_PRIORITY_HIGHEST`.

- Fornece-se um heap e um thread dedicado para executar a coleta de lixo para cada CPU, e os heaps são coletados ao mesmo tempo. Cada heap contém um heap de objeto pequeno e um heap de objeto grande, e todos os heaps podem ser acessados pelo código do usuário. Objetos em heaps diferentes podem fazer referência entre si.

- Como vários threads de coleta de lixo funcionam em conjunto, a coleta de lixo de servidor é mais rápida do que a coleta de lixo de estação de trabalho no heap de mesmo tamanho.

- Geralmente, a coleta de lixo de servidor tem segmentos maiores. No entanto, trata-se apenas de uma generalização: o tamanho do segmento é específico da implementação e está sujeito a alterações. Não faça suposições sobre o tamanho dos segmentos alocados pelo coletor de lixo ao sintonizar seu aplicativo.

- A coleta de lixo de servidor pode usar bastante recursos. Por exemplo, imagine que existem 12 processos que usam o servidor GC em execução em um computador que tem 4 processadores. Se todos os processos acontecerem de coletar lixo ao mesmo tempo, eles interfeririam uns com os outros, pois haveria 12 threads programados no mesmo processador. Se os processos estão ativos, não é uma boa idéia tê-los todos usando o servidor GC.

Se você está executando centenas de instâncias de um aplicativo, considere usar a coleta de lixo da estação de trabalho com coleta de lixo simultânea desativada. Isso resultará na redução da comutação de contexto, o que pode melhorar o desempenho.

## <a name="background-workstation-garbage-collection"></a>Coleta de lixo de estação de trabalho em segundo plano

Na coleta de lixo da estação de trabalho de fundo, as gerações efêmeras (0 e 1) são coletadas conforme necessário enquanto a coleta da geração 2 está em andamento. A coleta de lixo da estação de trabalho de fundo é realizada em um segmento dedicado e aplica-se apenas às coleções de geração 2.

A coleta de lixo em segundo plano é ativada por padrão e pode ser ativada ou desativada com a configuração [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) em aplicativos .NET Framework ou na configuração [System.GC.Simultaneamente](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) em aplicativos .NET Core.

> [!NOTE]
> A coleta de lixo em segundo plano substitui [a coleta de lixo simultânea](#concurrent-garbage-collection) e está disponível nas versões .NET Framework 4 e posteriores. No Quadro .NET 4, ele é suportado apenas para coleta de lixo de estações de trabalho. A partir do .NET Framework 4.5, a coleta de lixo em segundo plano está disponível tanto para a coleta de lixo da estação de trabalho quanto para o servidor.

Uma coleta em gerações efêmeras durante a coleta de lixo em segundo plano é conhecida como coleta de lixo em primeiro plano. Quando as coletas de lixo em primeiro plano ocorrem, todos os threads gerenciados são suspensos.

Quando a coleta de lixo de fundo está em andamento e você alocou objetos suficientes na geração 0, a CLR realiza uma coleta de lixo de geração 0 ou geração 1 em primeiro plano. O thread dedicado de coleta de lixo em segundo plano verifica em pontos frequentes de segurança se há uma solicitação de coleta de lixo em primeiro plano. Se houver, a coleta de plano de fundo suspende a si mesma para que a coleta de lixo em primeiro plano possa ocorrer. Após a coleta de lixo em primeiro plano, o thread dedicado de coleta de lixo em segundo plano e os threads de usuário continuam.

A coleta de lixo em segundo plano remove as restrições de alocação impostas pela coleta de lixo simultânea, pois as coletas de lixo efêmeras podem ocorrer durante a coleta de lixo em segundo plano. A coleta de lixo de fundo pode remover objetos mortos em gerações efêmeras. Também pode expandir o monte se necessário durante uma coleta de lixo de geração 1.

A ilustração a seguir mostra a coleta de lixo em segundo plano executada em um thread dedicado separado em uma estação de trabalho:

![Coleta de lixo de estação de trabalho em segundo plano](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Coleta de lixo de servidor em segundo plano

Começando com o .NET Framework 4.5, a coleta de lixo do servidor em segundo plano é o modo padrão para coleta de lixo do servidor.

A coleta de lixo do servidor em segundo plano funciona de forma semelhante à coleta de lixo em segundo plano, descrita na seção anterior, mas há algumas diferenças:

- A coleta de lixo de base da estação de trabalho usa um segmento dedicado de coleta de lixo em segundo plano, enquanto a coleta de lixo do servidor em segundo plano usa vários threads. Normalmente, há um segmento dedicado para cada processador lógico.

- Ao contrário do thread de coleta de lixo de estação de trabalho em segundo plano, esses threads não têm tempo limite.

A ilustração a seguir mostra a coleta de lixo em segundo plano executada em um thread dedicado separado em um servidor:

![Coleta de lixo de servidor em segundo plano](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Coleta de lixo simultânea

> [!TIP]
> Esta seção aplica-se a:
>
> - .NET Framework 3.5 e anteriormente para coleta de lixo de estação de trabalho
> - .NET Framework 4 e anteriorpara coleta de lixo do servidor
>
> O lixo simultâneo é substituído pela [coleta de lixo de fundo](#background-workstation-garbage-collection) em versões posteriores.

Na coleta de lixo de estação de trabalho ou servidor, você pode [habilitar a coleta simultânea](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)de lixo, o que permite que os threads funcionem simultaneamente com um segmento dedicado que realiza a coleta de lixo durante a maior parte da duração da coleta. Essa opção afeta apenas as coletas de lixo na geração 2. As gerações 0 e 1 são sempre não simultâneas, pois terminarem muito rápido.

A coleta de lixo simultânea permite que aplicativos interativos sejam mais responsivos minimizando a pausa para uma coleta. Na maioria das vezes, a execução dos threads gerenciados pode continuar enquanto o thread de coleta de lixo simultânea estiver em execução. Isso resulta em pausas menores enquanto uma coleta de lixo estiver em execução.

A coleta de lixo simultânea é executada em um thread dedicado. Por padrão, o CLR executa a coleta de lixo de estação de trabalho com a coleta de lixo simultânea habilitada. Isso é verdadeiro para computadores com processador único e vários processadores.

A ilustração a seguir mostra a coleta de lixo simultânea executada em um thread dedicado separado.

![Fios de coleta de lixo simultâneos](./media/gc-concurrent.png)

## <a name="see-also"></a>Confira também

- [Opções de configuração para GC](../../core/run-time-config/garbage-collector.md)
- [Coleta de lixo](index.md)
