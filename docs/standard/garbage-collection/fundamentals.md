---
title: Noções básicas da coleta de lixo
description: Saiba como o coletor de lixo funciona e como ele pode ser configurado para ter um desempenho ideal.
ms.date: 03/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background garbage collection
- garbage collection, concurrent garbage collection
- garbage collection, server garbage collection
- garbage collection, workstation garbage collection
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
ms.openlocfilehash: 840fe972192c6beb5d84017c288455f1cdf52177
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121241"
---
# <a name="fundamentals-of-garbage-collection"></a>Noções básicas da coleta de lixo

<a name="top"></a> No CLR (Common Language Runtime), o coletor de lixo atua como um gerenciador automático de memória. Ele oferece os seguintes benefícios:

- Permite que você desenvolva seu aplicativo sem precisar liberar a memória manualmente para objetos criados.

- Aloca objetos no heap gerenciado com eficiência.

- Recupera os objetos que não estão sendo usados, limpa a memória e mantém a memória disponível para alocações futuras. Os objetos gerenciados obtêm automaticamente conteúdo limpo com o qual começar, portanto, seus construtores não precisam inicializar cada campo de dados.

- Fornece segurança de memória, assegurando que um objeto não possa usar o conteúdo de outro objeto.

 Este tópico descreve os principais conceitos da coleta de lixo.

<a name="fundamentals_of_memory"></a>

## <a name="fundamentals-of-memory"></a>Conceitos básicos de memória

A lista a seguir resume conceitos importantes de memória do CLR.

- Cada processo tem seu próprio espaço de endereço virtual separado. Todos os processos no mesmo computador compartilham a mesma memória física e arquivo de paginação, se houver algum.

- Por padrão, em computadores de 32 bits, cada processo tem um espaço de endereço virtual no modo de usuário de 2 GB.

- Como desenvolvedor de aplicativos, você trabalha apenas com o espaço de endereço virtual e nunca manipula a memória física diretamente. O coletor de lixo aloca e libera memória virtual para você no heap gerenciado.

  Se você estiver escrevendo um código nativo, use as funções de Win32 para trabalhar com o espaço de endereço virtual. Essas funções alocam e liberam memória virtual para você em heaps nativos.

- A memória virtual pode estar em três estados:

  - Livre. O bloco de memória não tem referências a ele e está disponível para alocação.

  - Reservado. O bloco de memória está disponível para seu uso e não pode ser usado para nenhuma outra solicitação de alocação. No entanto, você não pode armazenar dados nesse bloco de memória até que ele esteja comprometido.

  - Comprometido. O bloco de memória é atribuído para armazenamento físico.

- O espaço de endereço virtual pode ficar fragmentado. Isso significa que há blocos livres, também conhecido como furos, no espaço de endereço. Quando uma alocação de memória virtual é solicitada, o gerenciador de memória virtual precisa localizar um único bloco livre suficientemente grande para atender a essa solicitação de alocação. Mesmo que você tenha 2 GB de espaço livre, a alocação que exige 2 GB não será bem-sucedida a menos que todo esse espaço livre esteja em um único bloco de endereço.

- Você poderá ficar sem memória se ficar sem espaço de endereço virtual para reservar ou espaço físico para confirmar.

O arquivo de paginação é usado, mesmo se a pressão de memória física (isto é, a demanda de memória física) é baixa. Na primeira vez em que a pressão de memória física estiver alta, o sistema operacional deverá liberar espaço na memória física para armazenar dados, além de fazer o backup de alguns dos dados na memória física para o arquivo de paginação. Esses dados não são paginados até que sejam necessários, portanto, é possível encontrar paginação em situações nas quais a pressão de memória física é muito baixa.

[Voltar ao início](#top)

<a name="conditions_for_a_garbage_collection"></a>

## <a name="conditions-for-a-garbage-collection"></a>Condições para uma coleta de lixo

A coleta de lixo ocorre quando uma das seguintes condições é verdadeira:

- O sistema tem pouca memória física. Isso é detectado pela notificação de falta de memória do sistema operacional, ou falta de memória indicada pelo host.

- A memória usada por objetos alocados no heap gerenciado ultrapassa o limite aceitável. Esse limite é ajustado continuamente enquanto o processo é executado.

- O método <xref:System.GC.Collect%2A?displayProperty=nameWithType> é chamado. Em quase todos os casos, você não precisa chamar esse método porque o coletor de lixo funciona continuamente. Esse método é usado principalmente para situações exclusivas e testes.

[Voltar ao início](#top)

<a name="the_managed_heap"></a>

## <a name="the-managed-heap"></a>O heap gerenciado

Depois que o coletor de lixo é inicializado pelo CLR, ele aloca um segmento da memória para armazenar e gerenciar objetos. Essa memória é chamada de heap gerenciado, em contraposição a um heap nativo no sistema operacional.

Há um heap gerenciado para cada processo gerenciado. Todos os threads no processo alocam memória para objetos no mesmo heap.

Para reservar memória, o coletor de lixo chama a função [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) de Win32 e reserva um segmento de memória por vez para aplicativos gerenciados. O coletor de lixo também reserva segmentos conforme o necessário, e libera segmentos de volta para o sistema operacional (depois de eliminar qualquer objeto) chamando a função [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) de Win32.

> [!IMPORTANT]
> O tamanho de segmentos alocados pelo coletor de lixo é específico da implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas. Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.

Quanto menos objetos alocados no heap, menos trabalho o coletor de lixo precisa fazer. Ao alocar objetos, não use valores arredondados que excedam suas necessidades, por exemplo, alocando uma matriz de 32 bytes quando são necessários apenas 15 bytes.

Quando uma coleta de lixo é disparada, o coletor de lixo recupera a memória ocupada por objetos inativos. O processo de recuperação compacta objetos vivos para que eles sejam movidos juntos e o espaço inativo é removido, tornando o heap menor. Isso garante que os objetos que são alocados juntos permaneçam juntos no heap gerenciado, para preservar sua localidade.

O grau de intrusão (frequência e a duração) de coletas de lixo é o resultado do volume de alocações e da quantidade de memória restante no heap gerenciado.

O heap pode ser considerado como o acúmulo de dois heaps: o [heap de objetos grandes](large-object-heap.md) e o heap de objetos pequenos.

O [heap de objetos grandes](large-object-heap.md) contém objetos muito grandes, com 85.000 bytes ou mais. Os objetos no heap de objetos grandes normalmente são matrizes. É raro que um objeto de instância seja muito grande.

[Voltar ao início](#top)

<a name="generations"></a>

## <a name="generations"></a>Gerações

O heap está organizado em gerações de modo que possa manipular objetos de vida útil longa e curta. A coleta de lixo ocorre principalmente com a recuperação de objetos de vida útil curta, que geralmente ocupam apenas uma pequena parte do heap. Há três gerações de objetos no heap:

- **Geração 0**. Essa é a geração mais jovem e contém objetos de vida útil curta. Um exemplo de um objeto de vida útil curta é uma variável temporária. A coleta de lixo ocorre com mais frequência nessa geração.

  Objetos alocados recentemente formam uma nova geração de objetos e, implicitamente, são coletas de geração 0, a menos que sejam objetos grandes; nesse caso, entram no heap de objetos grandes em uma coleta de geração 2.

  A maioria dos objetos são recuperados para coleta de lixo na geração 0 e não sobrevivem para a próxima geração.

- **Geração 1**. Essa geração contém objetos de vida útil curta e serve como um buffer entre objetos de vida útil curta e longa.

- **Geração 2**. Essa geração contém objetos de vida útil longa. Um exemplo de um objeto de vida útil longa é um objeto em um aplicativo para servidores que contém dados estáticos que estão vivos durante o processo.

Coletas de lixo ocorrem em gerações específicas conforme as condições permitirem. Coletar uma geração significa coletar objetos nessa geração e todas as suas gerações mais jovens. Uma coleta de lixo da geração 2 também é conhecida como uma coleta de lixo completa, pois ela recupera todos os objetos em todas as gerações (ou seja, todos os objetos no heap gerenciado).

### <a name="survival-and-promotions"></a>Sobrevivência e promoções

Objetos que não são recuperados em uma coleta de lixo são os sobreviventes e são promovidos à próxima geração. Objetos que sobrevivem a uma coleta de lixo da geração 0 são promovidos à geração 1; objetos que sobrevivem a uma coleta de lixo da geração 1 são promovidos à geração 2 e objetos que sobrevivem a uma coleta de lixo da geração 2 permanecem na geração 2.

Quando o coletor de lixo detecta que a taxa de sobrevivência é alta em uma geração ele aumenta o limite de alocações para a geração em questão, de modo que a próxima coleta obtém um tamanho substancial de memória recuperado. O CLR balanceia continuamente duas prioridades: não permitir que o conjunto de trabalho de um aplicativo fique muito grande atrasando a coleta de lixo e não permitindo que a coleta de lixo seja executada com muita frequência.

### <a name="ephemeral-generations-and-segments"></a>Gerações e segmentos efêmeros

Devido ao fato de os objetos em gerações 0 e 1 serem de vida útil curta, essas gerações são conhecidas como as gerações efêmeras.

As gerações efêmeras devem ser alocadas no segmento de memória que é conhecido como o segmento efêmero. Cada novo segmento adquirido pelo coletor de lixo torna-se o novo segmento efêmero e contém os objetos que sobreviveram a uma coleta de lixo da geração 0. O segmento efêmero antigo torna-se o novo segmento da geração 2.

O tamanho do segmento efêmero varia dependendo se um sistema for de 32 ou 64 bits, e no tipo de coletor de lixo que está em execução. Os valores padrão são mostrados na tabela a seguir.

||32 bits|64 bits|
|-|-------------|-------------|
|GC da estação de trabalho|16 MB|256 MB|
|GC do servidor|64 MB|4 GB|
|GC do Servidor com > 4 CPUs lógicas|32 MB|2 GB|
|GC do Servidor com > 8 CPUs lógicas|16 MB|1 GB|

O segmento efêmero pode incluir objetos da geração 2. Objetos da geração 2 podem usar vários segmentos (tantos quanto exigido pelo seu processo e permitido pela memória).

A quantidade de memória liberada de uma coleta de lixo efêmera é limitada ao tamanho do segmento efêmero. A quantidade de memória liberada é proporcional ao espaço que era ocupado pelos objetos inativos.

[Voltar ao início](#top)

<a name="what_happens_during_a_garbage_collection"></a>

## <a name="what-happens-during-a-garbage-collection"></a>O que ocorre durante uma coleta de lixo

Uma coleta de lixo tem as seguintes fases:

- Uma fase de marcação que localiza todos os objetos vivos e cria uma lista desses objetos.

- Uma fase de relocação que atualiza as referências aos objetos que serão compactados.

- Uma fase de compactação que recupera o espaço ocupado por objetos inativos e compacta os objetos sobreviventes. A fase de compactação move objetos que sobreviveram a uma coleta de lixo em direção à extremidade mais antiga do segmento.

  Em virtude das coletas da geração 2 poderem ocupar vários segmentos, objetos que são promovidos para a geração 2 podem ser movidos para um segmento mais antigo. Tanto os sobreviventes da geração 1 quanto da geração 2 podem ser movidos para um segmento diferente, porque eles são promovidos para a geração 2.

  Normalmente o heap de objetos grandes não é compactado, porque copiar objetos grandes causa uma penalidade de desempenho. No entanto, do .NET Framework 4.5.1 em diante, você pode usar a propriedade <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> para compactar o heap de objeto grande sob demanda.

O coletor de lixo usa as informações a seguir para determinar se os objetos estão vivos:

- **Raízes de pilha**. Variáveis de pilha fornecidas pelo compilador JIT (just-in-time) e movimentador de pilhas. As otimizações JIT podem aumentar ou diminuir as regiões de código dentro das quais as variáveis de pilha são relatadas para o coletor de lixo.

- **Identificadores de coleta de lixo**. Identificadores que apontam para objetos gerenciados e que podem ser alocados pelo código do usuário ou pelo Common Language Runtime.

- **Dados estáticos**. Objetos estáticos em domínios de aplicativo que podem fazer referência a outros objetos. Cada domínio de aplicativo controla seus objetos estáticos.

Antes de iniciar uma coleta de lixo, todos os threads gerenciados são suspensos, exceto o thread que disparou a coleta de lixo.

A ilustração a seguir mostra um thread que dispara uma coleta de lixo e faz com que outros threads sejam suspensos.

![Quando um thread dispara uma coleta de lixo](../../../docs/standard/garbage-collection/media/gc-triggered.png "Quando um thread dispara uma coleta de lixo")

[Voltar ao início](#top)

<a name="manipulating_unmanaged_resources"></a>

## <a name="manipulating-unmanaged-resources"></a>Manipulação de recursos não gerenciados

Se os objetos gerenciados referenciarem objetos não gerenciados por meio do uso de seus identificadores de arquivo nativo, você deverá liberar explicitamente os objetos não gerenciados, porque o coletor de lixo rastreia a memória somente no heap gerenciado.

Os usuários do seu objeto gerenciado não podem descartar os recursos nativos usados pelo objeto. Para executar a limpeza, você pode tornar o objeto gerenciado finalizável. A finalização consiste em ações de limpeza que são executadas quando o objeto não está mais em uso. Quando o objeto gerenciado é desativado, ele executa ações de limpeza que são especificadas em seu método finalizador.

Quando é descoberto que um objeto finalizável está inativo, seu finalizador é colocado em uma fila para que suas ações de limpeza sejam executadas, mas o próprio objeto é promovido para a próxima geração. Portanto, você precisa esperar até a próxima coleta de lixo ocorrer nessa geração (que não é necessariamente a próxima coleta de lixo) para determinar se o objeto foi recuperado.

[Voltar ao início](#top)

<a name="workstation_and_server_garbage_collection"></a>

## <a name="workstation-and-server-garbage-collection"></a>Coleta de lixo de estação de trabalho ou de servidor

O coletor de lixo tem autoajuste e pode trabalhar em uma ampla variedade de cenários. Você pode usar uma definição de arquivo de configuração para definir o tipo de coleta de lixo com base nas características da carga de trabalho. O CLR fornece os seguintes tipos de coleta de lixo:

- Coleta de lixo de estação de trabalho, que serve para todas as estações de trabalho cliente e computadores autônomos. Essa é a configuração padrão para o [\<elemento gcServer>](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) no esquema de configuração de tempo de execução.

  A coleta de lixo da estação de trabalho pode ser simultânea ou não simultânea. A coleta de lixo simultânea permite que os threads gerenciados continuem as operações durante uma coleta de lixo.

  A partir do .NET Framework 4, a coleta de lixo em segundo plano substitui a coleta de lixo simultânea.

- A coleta de lixo de servidor, que serve para aplicativos de servidor que precisam de escalabilidade e taxa de transferência altas. A coleta de lixo de servidor pode ser não simultânea ou em segundo plano.

A ilustração a seguir mostra os threads dedicados que executam a coleta de lixo em um servidor.

![Threads de coleta de lixo do servidor](../../../docs/standard/garbage-collection/media/gc-server.png "Threads de coleta de lixo do servidor")

### <a name="configuring-garbage-collection"></a>Configurar a coleta de lixo

Você pode usar o [\<elemento gcServer>](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) do esquema de configuração de tempo de execução para especificar o tipo de coleta de lixo que o CLR deve executar. Quando o atributo `enabled` desse elemento é definido como `false` (padrão), o CLR executa a coleta de lixo de estação de trabalho. Quando você define o atributo `enabled` como `true`, o CLR executa a coleta de lixo do servidor.

A coleta de lixo simultânea é especificada com o elemento [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do esquema de configuração de tempo de execução. A configuração padrão é `enabled`. Essa configuração controla a coleta de lixo simultânea e em segundo plano.

Você também pode especificar a coleta de lixo do servidor com interfaces de hospedagem não gerenciadas. Observe que o ASP.NET e o SQL Server permitem a coleta de lixo de servidor automaticamente se o aplicativo estiver hospedado em um desses ambientes.

### <a name="comparing-workstation-and-server-garbage-collection"></a>Comparação da coleta de lixo de estação de trabalho e de servidor

Veja a seguir considerações de desempenho e de threading para a coleta de lixo da estação de trabalho:

- A coleção ocorre no thread do usuário que disparou a coleta de lixo e permanece com a mesma prioridade. Como os threads de usuário normalmente são executados com prioridade normal, o coletor de lixo (que é executado em um thread de prioridade normal) deve disputam competir outros threads por tempo da CPU.

  O threads que estão executando o código nativo não são suspensos.

- A coleta de lixo de estação de trabalho é sempre usada em um computador que tem apenas um processador, independentemente da configuração [\<gcServer>](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md). Se você especificar a coleta de lixo de servidor, o CLR usará a coleta de lixo de estação de trabalho com a simultaneidade desabilitada.

Veja a seguir considerações de desempenho e de threading para a coleta de lixo de servidor:

- A coleta ocorre em vários threads dedicados que estão em execução no nível de prioridade `THREAD_PRIORITY_HIGHEST`.

- Fornece-se um heap e um thread dedicado para executar a coleta de lixo para cada CPU, e os heaps são coletados ao mesmo tempo. Cada heap contém um heap de objeto pequeno e um heap de objeto grande, e todos os heaps podem ser acessados pelo código do usuário. Objetos em heaps diferentes podem fazer referência entre si.

- Como vários threads de coleta de lixo funcionam em conjunto, a coleta de lixo de servidor é mais rápida do que a coleta de lixo de estação de trabalho no heap de mesmo tamanho.

- Geralmente, a coleta de lixo de servidor tem segmentos maiores. No entanto, observe que isso é apenas uma generalização: o tamanho do segmento é específico à implementação e está sujeito a alterações. Não faça suposição sobre o tamanho dos segmentos alocados pelo coletor de lixo ao ajustar seu aplicativo.

- A coleta de lixo de servidor pode usar bastante recursos. Por exemplo, se você tiver 12 processos em execução em um computador que tem 4 processadores, haverá 48 threads de coleta de lixo dedicados se todos estiverem usando a coleta de lixo de servidor. Em uma situação de carga de memória alta, se todos os processos começarem a realizar a coleta de lixo, o coletor de lixo terá 48 threads para agendar.

Se você estiver executando centenas de instâncias de um aplicativo, considere o uso da coleta de lixo de estação de trabalho com a coleta de lixo simultânea desabilitada. Isso resultará na redução da comutação de contexto, o que pode melhorar o desempenho.

[Voltar ao início](#top)

<a name="concurrent_garbage_collection"></a>

## <a name="concurrent-garbage-collection"></a>Coleta de lixo simultânea

Na coleta de lixo de estação de trabalho ou de servidor, você pode habilitar a coleta de lixo simultânea, o que permite que os threads executem simultaneamente a um thread dedicado que executa a coleta de lixo durante a maior parte da coleta. Essa opção afeta apenas as coletas de lixo na geração 2. As gerações 0 e 1 são sempre não simultâneas, pois terminarem muito rápido.

A coleta de lixo simultânea permite que aplicativos interativos sejam mais responsivos minimizando a pausa para uma coleta. Na maioria das vezes, a execução dos threads gerenciados pode continuar enquanto o thread de coleta de lixo simultânea estiver em execução. Isso resulta em pausas menores enquanto uma coleta de lixo estiver em execução.

Para melhorar o desempenho quando vários processos estiverem em execução, desabilite a coleta de lixo simultânea. Faça isso adicionando um [\<elemento gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) ao arquivo de configuração do aplicativo e definindo o valor de seu atributo `enabled` como `"false"`.

A coleta de lixo simultânea é executada em um thread dedicado. Por padrão, o CLR executa a coleta de lixo de estação de trabalho com a coleta de lixo simultânea habilitada. Isso é verdadeiro para computadores com processador único e vários processadores.

Sua capacidade de alocar pequenos objetos no heap durante uma coleta de lixo simultânea é limitada pelos objetos deixados no segmento efêmero quando uma coleta de lixo simultânea começa. Assim que você chegar ao fim do segmento, terá que aguardar a coleta de lixo simultânea terminar, enquanto os threads gerenciados que devem fazer as alocações de objeto pequeno estiverem suspensos.

A coleta de lixo simultânea tem um conjunto de trabalho ligeiramente maior (em comparação com a coleta de lixo não simultânea), pois você pode alocar objetos durante a coleta simultânea. No entanto, isso pode afetar o desempenho, pois os objetos que você aloca se tornam parte de seu conjunto de trabalho. Essencialmente, a coleta de lixo simultânea negocia CPU e memória para pausas mais curtas.

A ilustração a seguir mostra a coleta de lixo simultânea executada em um thread dedicado separado.

![Threads de coleta de lixo simultâneos](../../../docs/standard/garbage-collection/media/gc-concurrent.png "Threads de coleta de lixo simultâneos")

[Voltar ao início](#top)

<a name="background_garbage_collection"></a>

## <a name="background-workstation-garbage-collection"></a>Coleta de lixo de estação de trabalho em segundo plano

A coleta de lixo em segundo plano substitui a coleta de lixo da estação de trabalho simultânea começando com o .NET Framework 4 e substitui a coleta de lixo do servidor simultâneo, começando com o .NET Framework 4,5.  Na coleta de lixo em segundo plano, as gerações efêmeras (0 e 1) são coletadas conforme o necessário, enquanto a coleta da geração 2 estiver em andamento. Ele é executado em um thread dedicado e é aplicável somente a coleções de geração 2. A coleta de lixo em segundo plano é habilitada automaticamente por padrão e pode ser habilitada ou desabilitada com a definição de configuração [\<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) em aplicativos .NET Framework. 

> [!NOTE]
> A coleta de lixo em segundo plano está disponível apenas no .NET Framework 4 e em versões posteriores. No .NET Framework 4, ela é compatível somente para a coleta de lixo de estação de trabalho. A partir do .NET Framework 4.5, a coleta de lixo em segundo plano está disponível para a coleta de lixo de estação de trabalho e de servidor.

Uma coleta em gerações efêmeras durante a coleta de lixo em segundo plano é conhecida como coleta de lixo em primeiro plano. Quando as coletas de lixo em primeiro plano ocorrem, todos os threads gerenciados são suspensos.

Quando a coleta de lixo em segundo plano está em andamento, e você já tiver alocado objetos suficientes na geração 0, o CLR executará uma coleta de lixo em primeiro plano de geração 0 ou geração 1. O thread dedicado de coleta de lixo em segundo plano verifica em pontos frequentes de segurança se há uma solicitação de coleta de lixo em primeiro plano. Se houver, a coleta de plano de fundo suspende a si mesma para que a coleta de lixo em primeiro plano possa ocorrer. Após a coleta de lixo em primeiro plano, o thread dedicado de coleta de lixo em segundo plano e os threads de usuário continuam.

A coleta de lixo em segundo plano remove as restrições de alocação impostas pela coleta de lixo simultânea, pois as coletas de lixo efêmeras podem ocorrer durante a coleta de lixo em segundo plano. Isso significa que a coleta de lixo em segundo plano pode remover objetos inativos nas gerações efêmeras, e também expandir o heap durante uma coleta de lixo de geração 1, se for necessário.

A ilustração a seguir mostra a coleta de lixo em segundo plano executada em um thread dedicado separado em uma estação de trabalho:

![Diagrama que mostra a coleta de lixo da estação de trabalho em segundo plano.](./media/fundamentals/background-workstation-garbage-collection.png "O diagrama mostra a coleta de lixo da estação de trabalho em segundo plano.")

[Voltar ao início](#top)

<a name="background_server_garbage_collection"></a>

## <a name="background-server-garbage-collection"></a>Coleta de lixo de servidor em segundo plano

A partir do .NET Framework 4.5, a coleta de lixo de servidor em segundo plano é o modo padrão de coleta de lixo de servidor. Para escolher esse modo, defina o atributo `enabled` do [\<elemento gcServer>](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) como `true` no esquema de configuração de tempo de execução. Esse modo funciona quase igual à coleta de lixo de estação de trabalho em segundo plano, descrita na seção anterior, mas há algumas diferenças. A coleta de lixo de estação de trabalho em segundo plano usa um thread dedicado de coleta de lixo em segundo plano, enquanto a coleta de lixo do servidor em segundo plano usa vários threads, um thread dedicado para cada processador lógico, normalmente. Ao contrário do thread de coleta de lixo de estação de trabalho em segundo plano, esses threads não têm tempo limite.

A ilustração a seguir mostra a coleta de lixo em segundo plano executada em um thread dedicado separado em um servidor:

![Diagrama que mostra a coleta de lixo do servidor em segundo plano.](./media/fundamentals/background-server-garbage-collection.png "O diagrama mostra a coleta de lixo do servidor em segundo plano.")

## <a name="see-also"></a>Consulte também

- [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
