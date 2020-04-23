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
ms.openlocfilehash: 1fdf7fcd61fb4bf9e8e0cbfe28842208f6eadd00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102431"
---
# <a name="fundamentals-of-garbage-collection"></a>Noções básicas da coleta de lixo

No tempo de execução da linguagem comum (CLR), o coletor de lixo (GC) serve como um gerenciador automático de memória. O coletor de lixo gerencia a alocação e liberação de memória para um aplicativo. Para desenvolvedores que trabalham com código gerenciado, isso significa que você não precisa escrever código para executar tarefas de gerenciamento de memória. O gerenciamento automático de memória pode eliminar problemas comuns, como esquecer de liberar um objeto e causar um vazamento de memória ou tentar acessar a memória de um objeto que já foi liberado.

Este artigo descreve os conceitos centrais da coleta de lixo.

## <a name="benefits"></a>Benefícios

O coletor de lixo oferece os seguintes benefícios:

- Libera os desenvolvedores de ter que liberar a memória manualmente.

- Aloca objetos no heap gerenciado com eficiência.

- Recupera os objetos que não estão sendo usados, limpa a memória e mantém a memória disponível para alocações futuras. Objetos gerenciados recebem automaticamente conteúdo limpo para começar, para que seus construtores não precisem inicializar cada campo de dados.

- Fornece segurança de memória, assegurando que um objeto não possa usar o conteúdo de outro objeto.

## <a name="fundamentals-of-memory"></a>Conceitos básicos de memória

A lista a seguir resume conceitos importantes de memória do CLR.

- Cada processo tem seu próprio espaço de endereço virtual separado. Todos os processos no mesmo computador compartilham a mesma memória física e o arquivo de página, se houver um.

- Por padrão, em computadores de 32 bits, cada processo tem um espaço de endereço virtual no modo de usuário de 2 GB.

- Como desenvolvedor de aplicativos, você trabalha apenas com o espaço de endereço virtual e nunca manipula a memória física diretamente. O coletor de lixo aloca e libera memória virtual para você no heap gerenciado.

  Se você estiver escrevendo código nativo, você usa funções do Windows para trabalhar com o espaço de endereço virtual. Essas funções alocam e liberam memória virtual para você em heaps nativos.

- A memória virtual pode estar em três estados:

  | Estado | Descrição |
  |---------|---------|
  | Grátis | O bloco de memória não tem referências a ele e está disponível para alocação. |
  | Reservado | O bloco de memória está disponível para seu uso e não pode ser usado para nenhuma outra solicitação de alocação. No entanto, você não pode armazenar dados nesse bloco de memória até que ele esteja comprometido. |
  | Confirmado | O bloco de memória é atribuído para armazenamento físico. |

- O espaço de endereço virtual pode ficar fragmentado. Isso significa que há blocos livres, também conhecido como furos, no espaço de endereço. Quando uma alocação de memória virtual é solicitada, o gerenciador de memória virtual precisa localizar um único bloco livre suficientemente grande para atender a essa solicitação de alocação. Mesmo que você tenha 2 GB de espaço livre, uma alocação que requer 2 GB será mal sucedida, a menos que todo esse espaço livre esteja em um único bloco de endereços.

- Você pode ficar sem memória se não houver espaço de endereço virtual suficiente para reservar ou espaço físico para se comprometer.

  O arquivo de página é usado mesmo que a pressão de memória física (ou seja, a demanda por memória física) seja baixa. A primeira vez que a pressão da memória física é alta, o sistema operacional deve abrir espaço na memória física para armazenar dados, e faz backup de alguns dos dados que estão na memória física para o arquivo da página. Esses dados não são paginados até que sejam necessários, então é possível encontrar paginação em situações onde a pressão da memória física é baixa.
  
### <a name="memory-allocation"></a>Alocação de memória

Quando você inicializa um novo processo, o runtime reserva uma região contígua de espaço de endereço para o processo. Esse espaço de endereço reservado é chamado de heap gerenciado. O heap gerenciado mantém um ponteiro para o endereço no qual o próximo objeto do heap será alocado. Inicialmente, esse ponteiro é definido como o endereço básico do heap gerenciado. Todos os tipos de referência são alocados no heap gerenciado. Quando um aplicativo cria o primeiro tipo de referência, a memória é alocada para o tipo no endereço base do heap gerenciado. Quando o aplicativo cria o próximo objeto, o coletor de lixo aloca memória para ele no espaço de endereço logo depois do primeiro objeto. Desde que exista espaço de endereço disponível, o coletor de lixo continua alocando espaço para novos objetos dessa maneira.

A alocação memória com base no heap gerenciado é mais rápida do que a alocação de memória não gerenciada. Como o tempo de execução aloca a memória de um objeto adicionando um valor a um ponteiro, é quase tão rápido quanto alocar memória da pilha. Além disso, como novos objetos que são alocados consecutivamente são armazenados contíguos no heap gerenciado, um aplicativo pode acessar os objetos rapidamente.

### <a name="memory-release"></a>Liberação de memória

O mecanismo de otimização do coletor de lixo determina o melhor momento para executar uma coleta com base nas alocações que estão sendo feitas. Quando o coletor de lixo executa uma coleta, ele libera a memória dos objetos que não estão mais sendo usados pelo aplicativo. Ele determina quais objetos não estão mais sendo usados examinando as *raízes*do aplicativo . As raízes de um aplicativo incluem campos estáticos, variáveis locais e parâmetros na pilha de um thread, além de registros de CPU. Cada raiz refere-se a um objeto no heap gerenciado ou é definida como nula. O coletor de lixo tem acesso à lista de raízes ativas mantidas pelo runtime e pelo compilador JIT (just-in-time). Usando esta lista, o coletor de lixo cria um gráfico que contém todos os objetos que são alcançáveis a partir das raízes.

Objetos que não estão no gráfico são inacessíveis a partir das raízes do aplicativo. O coletor de lixo considera lixo de objetos inalcançáveis e libera a memória alocada para eles. Durante uma coleta, o coletor de lixo examina o heap gerenciado, procurando os blocos de espaço de endereço ocupados por objetos inacessíveis. Na medida em que descobre cada objeto inacessível, ele usa uma função de cópia de memória para compactar os objetos acessíveis na memória, liberando os blocos de espaços de endereço alocados para objetos inacessíveis. Uma vez que a memória dos objetos acessíveis tenha sido compactada, o coletor de lixo faz as correções necessárias no ponteiro de forma que as raízes do aplicativo apontem para os objetos em seus novos locais. Ele também posiciona o ponteiro do heap gerenciado após o último objeto acessível.

A memória só é compactada se uma coleção descobrir um número significativo de objetos inalcançáveis. Se todos os objetos no heap gerenciado sobrevivem a uma coleta, não há necessidade de compactação de memória.

Para melhorar o desempenho, o runtime aloca memória para objetos grandes em um heap separado. O coletor de lixo automaticamente libera a memória para objetos grandes. No entanto, para evitar mover objetos grandes na memória, essa memória geralmente não é compactada.

## <a name="conditions-for-a-garbage-collection"></a>Condições para uma coleta de lixo

A coleta de lixo ocorre quando uma das seguintes condições é verdadeira:

- O sistema tem pouca memória física. Isso é detectado pela notificação de memória baixa do SISTEMA OPERACIONAL ou pela memória baixa, conforme indicado pelo host.

- A memória usada por objetos alocados no monte gerenciado supera um limite aceitável. Esse limite é ajustado continuamente enquanto o processo é executado.

- O método <xref:System.GC.Collect%2A?displayProperty=nameWithType> é chamado. Em quase todos os casos, você não precisa chamar esse método, porque o coletor de lixo funciona continuamente. Esse método é usado principalmente para situações exclusivas e testes.

## <a name="the-managed-heap"></a>O heap gerenciado

Depois que o coletor de lixo é inicializado pelo CLR, ele aloca um segmento da memória para armazenar e gerenciar objetos. Essa memória é chamada de heap gerenciado, em contraposição a um heap nativo no sistema operacional.

Há um heap gerenciado para cada processo gerenciado. Todos os threads no processo alocam memória para objetos no mesmo heap.

Para reservar memória, o coletor de lixo chama a função Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) e reserva um segmento de memória por vez para aplicativos gerenciados. O coletor de lixo também reserva segmentos, conforme necessário, e libera segmentos de volta ao sistema operacional (depois de limpá-los de quaisquer objetos) chamando a função [Windows VirtualFree.](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)

> [!IMPORTANT]
> O tamanho de segmentos alocados pelo coletor de lixo é específico da implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas. Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.

Quanto menos objetos alocados no heap, menos trabalho o coletor de lixo precisa fazer. Quando você aloca objetos, não use valores arredondados que excedam suas necessidades, como alocar uma matriz de 32 bytes quando você precisar de apenas 15 bytes.

Quando uma coleta de lixo é acionada, o coletor de lixo recupera a memória que é ocupada por objetos mortos. O processo de recuperação compacta objetos vivos para que eles sejam movidos juntos e o espaço inativo é removido, tornando o heap menor. Isso garante que os objetos que estão alocados juntos permaneçam juntos no monte gerenciado para preservar sua localidade.

O grau de intrusão (frequência e a duração) de coletas de lixo é o resultado do volume de alocações e da quantidade de memória restante no heap gerenciado.

O heap pode ser considerado como o acúmulo de dois heaps: o [heap de objetos grandes](large-object-heap.md) e o heap de objetos pequenos. O grande monte de objetos contém objetos que são 85.000 bytes e maiores, que geralmente são matrizes. É raro um objeto de exemplo ser extremamente grande.

> [!TIP]
> Você pode [configurar o tamanho do limiar](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) para os objetos irem no heap de objeto grande.

## <a name="generations"></a>Gerações

O algoritmo GC é baseado em várias considerações:

- É mais rápido compactar a memória para uma parte do monte gerenciado do que para todo o monte gerenciado.
- Objetos mais novos têm vida útil mais curta e objetos mais antigos têm vida útil mais longa.
- Objetos mais novos tendem a ser relacionados uns com os outros e acessados pelo aplicativo ao mesmo tempo.

A coleta de lixo ocorre principalmente com a recuperação de objetos de curta duração. Para otimizar o desempenho do coletor de lixo, o monte gerenciado é dividido em três gerações, 0, 1 e 2, para que possa lidar com objetos de longa duração e de curta duração separadamente. O coletor de lixo armazena novos objetos na geração 0. Os objetos criados no início no tempo de vida do aplicativo que sobrevivem a coleções são promovidos e armazenados nas gerações 1 e 2. Como é mais rápido compactar uma parte do monte gerenciado do que todo o monte, este esquema permite que o coletor de lixo libere a memória em uma geração específica em vez de liberar a memória para todo o monte gerenciado cada vez que realiza uma coleta.

- **Geração 0**. Essa é a geração mais jovem e contém objetos de vida útil curta. Um exemplo de um objeto de vida útil curta é uma variável temporária. A coleta de lixo ocorre com mais frequência nessa geração.

  Objetos recém-alocados formam uma nova geração de objetos e são implicitamente coleções de geração 0. No entanto, se eles são objetos grandes, eles vão sobre o grande monte de objetos em uma coleção de geração 2.

  A maioria dos objetos são recuperados para coleta de lixo na geração 0 e não sobrevivem para a próxima geração.
  
  Se um aplicativo tentar criar um novo objeto quando a geração 0 estiver cheia, o coletor de lixo realiza uma coleta na tentativa de liberar espaço de endereço para o objeto. O coletor de lixo inicia examinando os objetos na geração 0 em vez de todos os objetos no heap gerenciado. Uma coleção de geração 0 sozinha muitas vezes recupera memória suficiente para permitir que o aplicativo continue criando novos objetos.

- **Geração 1**. Essa geração contém objetos de vida útil curta e serve como um buffer entre objetos de vida útil curta e longa.

  Depois que o coletor de lixo realiza uma coleta de geração 0, compacta a memória dos objetos alcançáveis e os promove à geração 1. Como os objetos que sobrevivem a coleções tendem a ter tempos de vida mais longos, faz sentido promovê-los a uma geração mais alta. O coletor de lixo não precisa reexaminar os objetos nas gerações 1 e 2 cada vez que realiza uma coleção de geração 0.
  
  Se uma coleção de geração 0 não recuperar memória suficiente para o aplicativo criar um novo objeto, o coletor de lixo pode realizar uma coleta de geração 1, então geração 2. Os objetos na geração 1 que sobrevivem a coleções são promovidos para a geração 2.

- **Geração 2**. Essa geração contém objetos de vida útil longa. Um exemplo de objeto de longa duração é um objeto em um aplicativo de servidor que contém dados estáticos que estão ativos durante a duração do processo.

  Objetos da geração 2 que sobrevivem a uma coleção permanecem na geração 2 até que sejam determinados como inalcançáveis em uma coleção futura.

Coletas de lixo ocorrem em gerações específicas conforme as condições permitirem. Coletar uma geração significa coletar objetos nessa geração e todas as suas gerações mais jovens. Uma coleta de lixo de geração 2 também é conhecida como uma coleta completa de lixo, pois recupera objetos em todas as gerações (ou seja, todos os objetos no monte gerenciado).

### <a name="survival-and-promotions"></a>Sobrevivência e promoções

Objetos que não são recuperados em uma coleta de lixo são conhecidos como sobreviventes e são promovidos para a próxima geração:

- Objetos que sobrevivem a uma geração 0 coleta de lixo são promovidos à geração 1.
- Objetos que sobrevivem a uma coleta de lixo de geração 1 são promovidos à geração 2.
- Objetos que sobrevivem a uma coleta de lixo de geração 2 permanecem na geração 2.

Quando o coletor de lixo detecta que a taxa de sobrevivência é alta em uma geração, aumenta o limiar de alocações para essa geração. A próxima coleção recebe um tamanho substancial de memória recuperada. A CLR equilibra continuamente duas prioridades: não deixar o conjunto de trabalho de um aplicativo ficar muito grande, atrasando a coleta de lixo e não deixando a coleta de lixo correr com muita freqüência.

### <a name="ephemeral-generations-and-segments"></a>Gerações e segmentos efêmeros

Como os objetos das gerações 0 e 1 são de curta duração, essas gerações são conhecidas como *as gerações efêmeras.*

Gerações efêmeras são alocadas no segmento de memória que é conhecido como o segmento efêmero. Cada novo segmento adquirido pelo coletor de lixo torna-se o novo segmento efêmero e contém os objetos que sobreviveram a uma coleta de lixo da geração 0. O segmento efêmero antigo torna-se o novo segmento da geração 2.

O tamanho do segmento efêmero varia dependendo se um sistema é de 32 bits ou 64 bits e sobre o tipo de coletor de lixo que está executando[(estação de trabalho ou servidor GC](workstation-server-gc.md)). A tabela a seguir mostra os tamanhos padrão do segmento efêmero.

|Estação de trabalho/servidor GC|32 bits|64 bits|
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

  Normalmente, o heap de objeto grande (LOH) não é compactado, porque copiar objetos grandes impõe uma penalidade de desempenho. No entanto, no .NET Core e no .NET Framework 4.5.1 e posterior, você pode usar a <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> propriedade para compactar o grande monte de objetos sob demanda. Além disso, o LOH é automaticamente compactado quando um limite rígido é definido especificando:

  - Um limite de memória em um recipiente.
  - As opções de configuração de tempo de execução [GCHeapHardLimitLimitLimitPercent.](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)

O coletor de lixo usa as informações a seguir para determinar se os objetos estão vivos:

- **Empilhar raízes**. Variáveis de pilha fornecidas pelo compilador JIT (just-in-time) e movimentador de pilhas. As otimizações do JIT podem alongar ou encurtar regiões de código dentro das quais as variáveis de pilha são relatadas ao coletor de lixo.

- **Alças de coleta de lixo**. Identificadores que apontam para objetos gerenciados e que podem ser alocados pelo código do usuário ou pelo Common Language Runtime.

- **Dados estáticos**. Objetos estáticos em domínios de aplicativo que podem fazer referência a outros objetos. Cada domínio de aplicativo controla seus objetos estáticos.

Antes de iniciar uma coleta de lixo, todos os threads gerenciados são suspensos, exceto o thread que disparou a coleta de lixo.

A ilustração a seguir mostra um thread que dispara uma coleta de lixo e faz com que outros threads sejam suspensos.

![Quando um segmento aciona uma coleta de lixo](./media/gc-triggered.png)

## <a name="unmanaged-resources"></a>Recursos não gerenciados

Para a maioria dos objetos que seu aplicativo cria, você pode contar com a coleta de lixo para executar automaticamente as tarefas de gerenciamento de memória necessárias. Entretanto, recursos não gerenciados requerem limpeza explícita. O tipo mais comum de recursos não gerenciados é um objeto que encapsula um recurso do sistema operacional, como um identificador de arquivo, um identificador de janela ou uma conexão de rede. Embora o coletor de lixo seja capaz de rastrear a vida útil de um objeto gerenciado que encapsula um recurso não gerenciado, ele não tem conhecimento específico sobre como limpar o recurso.

Quando você cria um objeto que encapsula um recurso não gerenciado, é recomendável que você forneça o código `Dispose` necessário para limpar o recurso não gerenciado em um método público. Ao fornecer um método `Dispose`, você permite que usuários do seu objeto liberem, explicitamente, sua memória quando terminarem o objeto. Quando você usar um objeto que encapsula um recurso não `Dispose` gerenciado, certifique-se de ligar conforme necessário.

Você também deve fornecer uma maneira para que seus recursos não gerenciados sejam `Dispose`liberados caso um consumidor do seu tipo esqueça de ligar . Você pode usar uma alça segura para envolver o recurso <xref:System.Object.Finalize?displayProperty=nameWithType> não gerenciado ou substituir o método.

Para obter mais informações sobre a limpeza de recursos não gerenciados, consulte [Limpar recursos não gerenciados](unmanaged.md).

## <a name="see-also"></a>Confira também

- [Coleta de lixo de estação de trabalho ou de servidor](workstation-server-gc.md)
- [Coleta de lixo de fundo](background-gc.md)
- [Opções de configuração para GC](../../core/run-time-config/garbage-collector.md)
- [Coleta de lixo](index.md)
