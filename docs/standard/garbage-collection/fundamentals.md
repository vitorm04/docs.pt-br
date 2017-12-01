---
title: "Noções básicas da coleta de lixo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background garbage collection
- garbage collection, concurrent garbage collection
- garbage collection, server garbage collection
- garbage collection, workstation garbage collection
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
caps.latest.revision: "51"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15ae041cdadb259c59d447b8775844fc96048be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="fundamentals-of-garbage-collection"></a>Noções básicas da coleta de lixo
<a name="top"></a>No common language runtime (CLR), o coletor de lixo atua como um Gerenciador de memória automática. Ele oferece os seguintes benefícios:  
  
-   Permite que você desenvolva seu aplicativo sem a necessidade de liberar memória.  
  
-   Aloca objetos no heap gerenciado com eficiência.  
  
-   Recupera os objetos que não estão sendo usados, limpa a memória e mantém a memória disponível para alocações futuras. Os objetos gerenciados obtêm automaticamente conteúdo limpo com o qual começar, portanto, seus construtores não precisam inicializar cada campo de dados.  
  
-   Fornece segurança de memória, assegurando que um objeto não possa usar o conteúdo de outro objeto.  
  
 Este tópico descreve os principais conceitos da coleta de lixo. Ele contém as seguintes seções:  
  
-   [Conceitos básicos de memória](#fundamentals_of_memory)  
  
-   [Condições para uma coleta de lixo](#conditions_for_a_garbage_collection)  
  
-   [O heap gerenciado](#the_managed_heap)  
  
-   [Gerações](#generations)  
  
-   [O que acontece durante uma coleta de lixo](#what_happens_during_a_garbage_collection)  
  
-   [Manipulação de recursos não gerenciados](#manipulating_unmanaged_resources)  
  
-   [Coleta de lixo de estação de trabalho e servidor](#workstation_and_server_garbage_collection)  
  
-   [Coleta de lixo simultânea](#concurrent_garbage_collection)  
  
-   [Coleta de lixo de estação de trabalho em segundo plano](#background_garbage_collection)  
  
-   [Coleta de lixo do servidor em segundo plano](#background_server_garbage_collection)  
  
<a name="fundamentals_of_memory"></a>   
## <a name="fundamentals-of-memory"></a>Conceitos básicos de memória  
 A lista a seguir resume conceitos importantes de memória do CLR.  
  
-   Cada processo tem seu próprio espaço de endereço virtual separado. Todos os processos no mesmo computador compartilham a mesma memória física e arquivo de paginação, se houver algum.  
  
-   Por padrão, em computadores de 32 bits, cada processo tem um espaço de endereço virtual no modo de usuário de 2 GB.  
  
-   Como desenvolvedor de aplicativos, você trabalha apenas com o espaço de endereço virtual e nunca manipula a memória física diretamente. O coletor de lixo aloca e libera memória virtual para você no heap gerenciado.  
  
     Se você estiver escrevendo o código nativo, você usar funções do Win32 para trabalhar com o espaço de endereço virtual. Essas funções alocam e liberar memória virtual para você em nativo heaps.  
  
-   A memória virtual pode estar em três estados:  
  
    -   Livre. O bloco de memória não tem referências a ele e está disponível para alocação.  
  
    -   Reservado. O bloco de memória está disponível para seu uso e não pode ser usado para nenhuma outra solicitação de alocação. No entanto, você não pode armazenar dados nesse bloco de memória até que ele esteja comprometido.  
  
    -   Comprometido. O bloco de memória é atribuído para armazenamento físico.  
  
-   O espaço de endereço virtual pode ficar fragmentado. Isso significa que há blocos livres, também conhecido como furos, no espaço de endereço. Quando uma alocação de memória virtual é solicitada, o gerenciador de memória virtual precisa localizar um único bloco livre suficientemente grande para atender a essa solicitação de alocação. Mesmo se você tiver 2 GB de espaço livre, a alocação que requer de 2 GB será malsucedida, a menos que todo esse espaço livre está em um bloco de endereço único.  
  
-   Você poderá ficar sem memória se ficar sem espaço de endereço virtual para reservar ou espaço físico para confirmar.  
  
 O arquivo de paginação é usado, mesmo se a pressão de memória física (isto é, a demanda de memória física) é baixa. Na primeira vez em que a pressão de memória física estiver alta, o sistema operacional deverá liberar espaço na memória física para armazenar dados, além de fazer o backup de alguns dos dados na memória física para o arquivo de paginação. Esses dados não são paginados até que sejam necessários, portanto, é possível encontrar paginação em situações nas quais a pressão de memória física é muito baixa. 
 
 [Voltar ao início](#top)  
  
<a name="conditions_for_a_garbage_collection"></a>   
## <a name="conditions-for-a-garbage-collection"></a>Condições para uma coleta de lixo  
 A coleta de lixo ocorre quando uma das seguintes condições é verdadeira:  
  
-   O sistema tem pouca memória física. Isso é detectado, a notificação de falta de memória do sistema operacional ou memória insuficiente indicado pelo host.
  
-   A memória usada por objetos alocados no heap gerenciado ultrapassa o limite aceitável. Esse limite é ajustado continuamente enquanto o processo é executado.  
  
-   O <xref:System.GC.Collect%2A?displayProperty=nameWithType> método é chamado. Em quase todos os casos, você não precisa chamar esse método porque o coletor de lixo funciona continuamente. Esse método é usado principalmente para situações exclusivas e testes.  
  
 [Voltar ao início](#top)  
  
<a name="the_managed_heap"></a>   
## <a name="the-managed-heap"></a>O heap gerenciado  
 Depois que o coletor de lixo é inicializado pelo CLR, ele aloca um segmento da memória para armazenar e gerenciar objetos. Essa memória é chamada de heap gerenciado, em contraposição a um heap nativo no sistema operacional.  
  
 Há um heap gerenciado para cada processo gerenciado. Todos os threads no processo alocam memória para objetos no mesmo heap.  
  
 Para reservar memória, o coletor de lixo chama o Win32 [VirtualAlloc](http://go.microsoft.com/fwlink/?LinkId=179047) função e as reservas de um segmento de memória em um horário para aplicativos gerenciados. O coletor de lixo também reserva segmentos conforme necessário e libera segmentos de volta para o sistema operacional (depois limpá-los de qualquer objeto) chamando o Win32 [VirtualFree](http://go.microsoft.com/fwlink/?LinkId=179050) função.  
  
> [!IMPORTANT]
>  O tamanho de segmentos alocados pelo coletor de lixo é específico da implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas. Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.  
  
 Quanto menos objetos alocados no heap, menos trabalho o coletor de lixo precisa fazer. Ao alocar objetos, não use valores arredondados que excedam suas necessidades, por exemplo, alocando uma matriz de 32 bytes quando são necessários apenas 15 bytes.  
  
 Quando uma coleta de lixo é disparada, o coletor de lixo recupera a memória ocupada por objetos inativos. O processo de recuperação compacta objetos vivos para que eles sejam movidos juntos e o espaço inativo é removido, tornando o heap menor. Isso garante que os objetos que são alocados juntos permaneçam juntos no heap gerenciado, para preservar sua localidade.  
  
 O grau de intrusão (frequência e a duração) de coletas de lixo é o resultado do volume de alocações e da quantidade de memória restante no heap gerenciado.  
  
 O heap pode ser considerado como o acúmulo de dois heaps: o heap de objetos grandes e o heap de objetos pequenos.  
  
 O heap de objetos grandes contém objetos muito grandes, com 85.000 bytes ou mais. Os objetos no heap de objetos grandes normalmente são matrizes. É raro que um objeto de instância seja muito grande.  
  
 [Voltar ao início](#top)  
  
<a name="generations"></a>   
## <a name="generations"></a>Gerações  
 O heap está organizado em gerações de modo que possa manipular objetos de vida útil longa e curta. A coleta de lixo ocorre principalmente com a recuperação de objetos de vida útil curta, que geralmente ocupam apenas uma pequena parte do heap. Há três gerações de objetos no heap:  
  
-   **Geração 0**. Essa é a geração mais jovem e contém objetos de vida útil curta. Um exemplo de um objeto de vida útil curta é uma variável temporária. A coleta de lixo ocorre com mais frequência nessa geração.  
  
     Objetos alocados recentemente formam uma nova geração de objetos e, implicitamente, são coletas de geração 0, a menos que sejam objetos grandes; nesse caso, entram no heap de objetos grandes em uma coleta de geração 2.  
  
     A maioria dos objetos são recuperados para coleta de lixo na geração 0 e não sobrevivem para a próxima geração.  
  
-   **Geração 1**. Essa geração contém objetos de vida útil curta e serve como um buffer entre objetos de vida útil curta e longa.  
  
-   **Geração 2**. Essa geração contém objetos de vida útil longa. Um exemplo de um objeto de vida útil longa é um objeto em um aplicativo para servidores que contém dados estáticos que estão vivos durante o processo.  
  
 Coletas de lixo ocorrem em gerações específicas conforme as condições permitirem. Coletar uma geração significa coletar objetos nessa geração e todas as suas gerações mais jovens. Uma coleta de lixo da geração 2 também é conhecida como uma coleta de lixo completa, pois ela recupera todos os objetos em todas as gerações (ou seja, todos os objetos no heap gerenciado).  
  
### <a name="survival-and-promotions"></a>Sobrevivência e promoções  
 Objetos que não são recuperados em uma coleta de lixo são os sobreviventes e são promovidos à próxima geração. Objetos que sobrevivem a uma coleta de lixo da geração 0 são promovidos à geração 1; objetos que sobrevivem a uma coleta de lixo da geração 1 são promovidos à geração 2 e objetos que sobrevivem a uma coleta de lixo da geração 2 permanecem na geração 2.  
  
 Quando o coletor de lixo detecta que a taxa de sobrevivência é alta em uma geração ele aumenta o limite de alocações para a geração em questão, de modo que a próxima coleta obtém um tamanho substancial de memória recuperado. O CLR equilibra continuamente duas prioridades: não permitir que o conjunto de trabalho de um aplicativo fique muito grande e não permitir que a coleta de lixo demore muito tempo.  
  
### <a name="ephemeral-generations-and-segments"></a>Gerações e segmentos efêmeros  
 Devido ao fato de os objetos em gerações 0 e 1 serem de vida útil curta, essas gerações são conhecidas como as gerações efêmeras.  
  
 As gerações efêmeras devem ser alocadas no segmento de memória que é conhecido como o segmento efêmero. Cada novo segmento adquirido pelo coletor de lixo torna-se o novo segmento efêmero e contém os objetos que sobreviveram a uma coleta de lixo da geração 0. O segmento efêmero antigo torna-se o novo segmento da geração 2.  
  
 O tamanho do segmento efêmero varia dependendo se é de um sistema de 32 ou 64 bits e o tipo de coletor de lixo está em execução. Valores padrão são mostrados na tabela a seguir.  
  
||32 bits|64 bits|  
|-|-------------|-------------|  
|Estação de trabalho GC|16 MB|256 MB|  
|Servidor GC|64 MB|4 GB|  
|Servidor GC com > 4 CPUs lógicas|32 MB|2 GB|  
|Servidor GC com > 8 CPUs lógicas|16 MB|1 GB|  
  
 O segmento efêmero pode incluir objetos da geração 2. Objetos da geração 2 podem usar vários segmentos (tantos quanto exigido pelo seu processo e permitido pela memória).  
  
 A quantidade de memória liberada de uma coleta de lixo efêmera é limitada ao tamanho do segmento efêmero. A quantidade de memória liberada é proporcional ao espaço que era ocupado pelos objetos inativos.  
  
 [Voltar ao início](#top)  
  
<a name="what_happens_during_a_garbage_collection"></a>   
## <a name="what-happens-during-a-garbage-collection"></a>O que ocorre durante uma coleta de lixo  
 Uma coleta de lixo tem as seguintes fases:  
  
-   Uma fase de marcação que localiza todos os objetos vivos e cria uma lista desses objetos.  
  
-   Uma fase de relocação que atualiza as referências aos objetos que serão compactados.  
  
-   Uma fase de compactação que recupera o espaço ocupado por objetos inativos e compacta os objetos sobreviventes. A fase de compactação move objetos que sobreviveram a uma coleta de lixo em direção à extremidade mais antiga do segmento.  
  
     Em virtude das coletas da geração 2 poderem ocupar vários segmentos, objetos que são promovidos para a geração 2 podem ser movidos para um segmento mais antigo. Tanto os sobreviventes da geração 1 quanto da geração 2 podem ser movidos para um segmento diferente, porque eles são promovidos para a geração 2.  
  
     Normalmente o heap de objetos grandes não é compactado, porque copiar objetos grandes causa uma penalidade de desempenho. No entanto, começando com o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], você pode usar o <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> propriedade compactar o heap de objeto grande sob demanda.  
  
 O coletor de lixo usa as informações a seguir para determinar se os objetos estão vivos:  
  
-   **Raízes de pilha**. Variáveis de pilha fornecidas pelo compilador JIT (just-in-time) e movimentador de pilhas.  
  
-   **Identificadores de coleta de lixo**. Trata-se de que aponte para objetos gerenciados e que podem ser alocados pelo código do usuário ou pelo common language runtime.  
  
-   **Dados estáticos**. Objetos estáticos em domínios de aplicativo que podem fazer referência a outros objetos. Cada domínio de aplicativo controla seus objetos estáticos.  
  
 Antes de iniciar uma coleta de lixo, todos os threads gerenciados são suspensos, exceto o thread que disparou a coleta de lixo.  
  
 A ilustração a seguir mostra um thread que dispara uma coleta de lixo e faz com que outros threads sejam suspensos.  
  
 ![Quando um thread dispara uma coleta de lixo](../../../docs/standard/garbage-collection/media/gc-triggered.png "GC_Triggered")  
Thread que dispara uma coleta de lixo  
  
 [Voltar ao início](#top)  
  
<a name="manipulating_unmanaged_resources"></a>   
## <a name="manipulating-unmanaged-resources"></a>Manipulação de recursos não gerenciados  
 Se os objetos gerenciados referenciarem objetos não gerenciados por meio do uso de seus identificadores de arquivo nativo, você deverá liberar explicitamente os objetos não gerenciados, porque o coletor de lixo rastreia a memória somente no heap gerenciado.  
  
 Os usuários do seu objeto gerenciado não podem descartar os recursos nativos usados pelo objeto. Para executar a limpeza, você pode tornar o objeto gerenciado finalizável. A finalização consiste em ações de limpeza que são executadas quando o objeto não está mais em uso. Quando o objeto gerenciado é desativado, ele executa ações de limpeza que são especificadas em seu método finalizador.  
  
 Quando é descoberto que um objeto finalizável está inativo, seu finalizador é colocado em uma fila para que suas ações de limpeza sejam executadas, mas o próprio objeto é promovido para a próxima geração. Portanto, você precisa esperar até a próxima coleta de lixo ocorrer nessa geração (que não é necessariamente a próxima coleta de lixo) para determinar se o objeto foi recuperado.  
  
 [Voltar ao início](#top)  
  
<a name="workstation_and_server_garbage_collection"></a>   
## <a name="workstation-and-server-garbage-collection"></a>Coleta de lixo de estação de trabalho e servidor  
 O coletor de lixo é auto-ajuste e podem trabalhar em uma ampla variedade de cenários. Você pode usar uma configuração de arquivo de configuração para definir o tipo de coleta de lixo com base nas características da carga de trabalho. O CLR fornece os seguintes tipos de coleta de lixo:  
  
-   Coleta de lixo de estação de trabalho, que é para todas as estações de trabalho cliente e computadores autônomos. Essa é a configuração padrão para o [ \<gcServer > elemento](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) no esquema de configuração de tempo de execução.  
  
     Coleta de lixo da estação de trabalho pode ser simultâneas ou não simultânea. Coleta de lixo simultânea permite que os threads gerenciados continuar as operações durante uma coleta de lixo.  
  
     Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], coleta de lixo em segundo plano substitui a coleta de lixo simultânea.  
  
-   Coleta de lixo de servidor, que destina-se a aplicativos de servidor que precisam de escalabilidade e alta taxa de transferência. Coleta de lixo do servidor pode ser não simultânea ou em segundo plano.  
  
 A ilustração a seguir mostra os threads dedicados que executam a coleta de lixo em um servidor.  
  
 ![Threads de coleta de lixo do servidor](../../../docs/standard/garbage-collection/media/gc-server.png "GC_Server")  
Coleta de lixo do servidor  
  
### <a name="configuring-garbage-collection"></a>Configurar a coleta de lixo  
 Você pode usar o [ \<gcServer > elemento](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) do esquema de configuração de tempo de execução para especificar o tipo de coleta de lixo desejado para executar o CLR. Quando esse elemento `enabled` atributo é definido como `false` (o padrão), o CLR executa a coleta de lixo de estação de trabalho. Quando você define o `enabled` atributo `true`, o CLR executa a coleta de lixo do servidor.  
  
 Coleta de lixo simultânea é especificada com o [ \<gcConcurrent > elemento](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do esquema de configuração de tempo de execução. A configuração padrão é `enabled`. Essa configuração controla os dois simultâneas e a coleta de lixo do plano de fundo.  
  
 Você também pode especificar a coleta de lixo do servidor com interfaces de hospedagem não gerenciados. Observe que ASP.NET e o SQL Server habilitar coleta de lixo do servidor automaticamente se o aplicativo é hospedado em um destes ambientes.  
  
### <a name="comparing-workstation-and-server-garbage-collection"></a>Comparando a coleta de lixo de estação de trabalho e servidor  
 As seguintes são considerações de desempenho e threading para coleta de lixo da estação de trabalho:  
  
-   A coleção ocorre no thread do usuário que disparou a coleta de lixo e permanece com a mesma prioridade. Como os threads de usuário normalmente são executados em prioridade normal, o coletor de lixo (que é executado em um thread de prioridade normal) deve disputam com outros threads de tempo de CPU.  
  
     Threads que estão executando o código nativo não são suspensos.  
  
-   Coleta de lixo da estação de trabalho é sempre usada em um computador que tem apenas um processador, independentemente do [ \<gcServer >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) configuração. Se você especificar a coleta de lixo do servidor, o CLR usa coleta de lixo da estação de trabalho com simultaneidade desabilitada.  
  
 As seguintes são considerações de desempenho e threading para coleta de lixo do servidor:  
  
-   A coleção ocorre em vários threads dedicados que são executados em `THREAD_PRIORITY_HIGHEST` nível de prioridade.  
  
-   Um heap e um thread dedicado para executar a coleta de lixo são fornecidos para cada CPU e pilhas são coletadas ao mesmo tempo. Cada heap contém um heap de objeto pequeno e um heap de objeto grande, e todos os heaps podem ser acessados pelo código do usuário. Objetos em heaps diferentes podem referir-se entre si.  
  
-   Como vários threads de coleta de lixo funcionam em conjunto, coleta de lixo do servidor é mais rápida que a coleta de lixo de estação de trabalho na mesma pilha de tamanho.  
  
-   Coleta de lixo do servidor geralmente tem segmentos de tamanho maior. No entanto, observe que isso é apenas uma generalização: tamanho do segmento é específico da implementação e está sujeita a alterações. Você não deve fazer nenhuma suposição sobre o tamanho de segmentos alocados pelo coletor de lixo no ajuste de seu aplicativo.  
  
-   Coleta de lixo do servidor pode ser uso intensivo de recursos. Por exemplo, se você tiver 12 processos em execução em um computador que tem 4 processadores, haverá 48 threads de coleta de lixo dedicado se eles estão usando coleta de lixo do servidor. Em uma situação de carga de memória alta, se todos os processos começar a fazer a coleta de lixo, o coletor de lixo terá 48 threads para agendar.  
  
 Se você estiver executando centenas de instâncias de um aplicativo, considere o uso de coleta de lixo da estação de trabalho com a coleta de lixo simultânea desabilitada. Isso resulta em menos alternância de contexto, que pode melhorar o desempenho.  
  
 [Voltar ao início](#top)  
  
<a name="concurrent_garbage_collection"></a>   
## <a name="concurrent-garbage-collection"></a>Coleta de lixo simultânea  
 Na coleta de lixo de estação de trabalho ou servidor, você pode habilitar a coleta de lixo simultânea, que permite que os threads para executar simultaneamente com um thread dedicado que executa a coleta de lixo na maior parte da duração da coleção. Essa opção afeta apenas as coletas de lixo de geração 2. as gerações 0 e 1 são sempre não simultâneas porque terminarem muito rápido.  
  
 Coleta de lixo simultânea permite que aplicativos interativos ser mais responsivo, minimizando a pausa para uma coleção. Threads gerenciados podem continuar sendo executado na maioria das vezes enquanto o thread de coleta de lixo simultânea está em execução. Isso resulta em menor pausa enquanto estiver ocorrendo uma coleta de lixo.  
  
 Para melhorar o desempenho quando vários processos estão em execução, desabilite a coleta de lixo simultânea. Você pode fazer isso adicionando um [ \<gcConcurrent > elemento](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) para o arquivo de configuração do aplicativo e definir o valor de seu `enabled` atributo `"false"`.  
  
 Coleta de lixo simultânea é executada em um thread dedicado. Por padrão, o CLR executa a coleta de lixo da estação de trabalho com coleta de lixo simultânea habilitada. Isso é verdadeiro para computadores com processador único e vários processadores.  
  
 A capacidade de alocar pequenos objetos no heap durante uma coleta de lixo simultânea é limitada pelos objetos permanecem no segmento efêmero quando inicia uma coleta de lixo simultânea. Assim que você chega ao fim do segmento, você terá que aguardar a coleta de lixo simultânea terminar enquanto estiverem suspenso threads gerenciados que deve fazer as alocações de objeto pequeno.  
  
 Coleta de lixo simultânea tem um conjunto de trabalho ligeiramente maior (em comparação com a coleta de lixo não simultânea), porque você pode alocar objetos durante a coleta de simultânea. No entanto, isso pode afetar o desempenho, porque os objetos que você alocar se tornam parte do seu conjunto de trabalho. Essencialmente, a coleta de lixo simultânea negocia alguns CPU e memória para pausa mais curto.  
  
 A ilustração a seguir mostra a coleta de lixo simultânea executada em um thread dedicado separado.  
  
 ![Threads de coleta de lixo simultânea](../../../docs/standard/garbage-collection/media/gc-concurrent.png "GC_Concurrent")  
Coleta de lixo simultânea  
  
 [Voltar ao início](#top)  
  
<a name="background_garbage_collection"></a>   
## <a name="background-workstation-garbage-collection"></a>Coleta de lixo de estação de trabalho em segundo plano  
 Na coleta de lixo em segundo plano, gerações efêmeras (0 e 1) são coletadas conforme necessário, enquanto a coleção de geração 2 está em andamento. Não há nenhuma configuração de coleta de lixo em segundo plano; ele é habilitado automaticamente com a coleta de lixo simultânea. Coleta de lixo em segundo plano é uma substituição para coleta de lixo simultânea. Como com a coleta de lixo simultânea, coleta de lixo em segundo plano é executada em um thread dedicado e é aplicável somente a coleções de geração 2.  
  
> [!NOTE]
>  Coleta de lixo em segundo plano está disponível apenas no [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] e versões posteriores. No [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], há suporte apenas para coleta de lixo da estação de trabalho. Começando com o .NET Framework 4.5, coleta de lixo em segundo plano está disponível para coleta de lixo de estação de trabalho e servidor.  
  
 Uma coleção de gerações efêmeras durante a coleta de lixo em segundo plano é conhecida como coleta de lixo de primeiro plano. Quando ocorrem as coletas de lixo de primeiro plano, todos os threads gerenciados são suspensos.  
  
 Quando a coleta de lixo em segundo plano está em andamento e você tem suficiente objetos alocados na geração 0, o CLR executa uma geração 0 ou a coleta de lixo da geração 1 em primeiro plano. Verifica se o thread de coleta de lixo em segundo plano dedicado em pontos frequentes de segurança para determinar se há uma solicitação de coleta de lixo de primeiro plano. Se houver, a coleção de plano de fundo suspende a próprio para que a coleta de lixo de primeiro plano pode ocorrer. Após a coleta de lixo de primeiro plano, o thread de coleta de lixo em segundo plano dedicado e threads de usuário retomar.  
  
 Coleta de lixo em segundo plano remove as restrições de alocação impostas pela coleta de lixo simultânea, porque as coletas de lixo efêmera podem ocorrer durante a coleta de lixo em segundo plano. Isso significa que a coleta de lixo em segundo plano pode remover objetos inativos nas gerações efêmeras e também pode expandir o heap se necessário durante uma coleta de lixo 1 de geração.  
  
 A ilustração a seguir mostra executada em um thread separado dedicado em uma estação de trabalho de coleta de lixo em segundo plano.  
  
 ![Coleta de lixo da estação de trabalho do plano de fundo](../../../docs/standard/garbage-collection/media/backgroundworkstn.png "BackgroundWorkstn")  
Coleta de lixo de estação de trabalho em segundo plano  
  
 [Voltar ao início](#top)  
  
<a name="background_server_garbage_collection"></a>   
## <a name="background-server-garbage-collection"></a>Coleta de lixo do servidor em segundo plano  
 Começando com o .NET Framework 4.5, coleta de lixo do servidor em segundo plano é o modo padrão para coleta de lixo do servidor. Para escolher este modo, defina o `enabled` atributo o [ \<gcServer > elemento](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) para `true` no esquema de configuração de tempo de execução. Essas funções de modo da mesma forma que a coleta de lixo de estação de trabalho em segundo plano, descrito na seção anterior, mas há algumas diferenças. Coleta de lixo de estação de trabalho em segundo plano usa um thread de coleta de lixo em segundo plano dedicado, enquanto a coleta de lixo do servidor em segundo plano usa vários threads, normalmente um thread dedicado para cada processador lógico. Ao contrário do thread de coleta de lixo de plano de fundo de estação de trabalho, esses threads não têm tempo limite.  
  
 A ilustração a seguir mostra executada em um thread separado dedicado em um servidor de coleta de lixo em segundo plano.  
  
 ![Coleta de lixo do servidor do plano de fundo](../../../docs/standard/garbage-collection/media/backgroundserver.png "BackgroundServer")  
Coleta de lixo do servidor em segundo plano  
  
## <a name="see-also"></a>Consulte também  
 [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
