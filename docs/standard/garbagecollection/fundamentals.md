---
title: "Noções básicas da coleta de lixo"
description: "Noções básicas da coleta de lixo"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9d5fce64-95a4-4609-8eee-b0ac70078cdb
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 02b0311559071147b38182076f60918b7351cc63
ms.lasthandoff: 03/02/2017

---

# <a name="fundamentals-of-garbage-collection"></a>Noções básicas da coleta de lixo

No tempo de execução do Common Language Runtime (CLR), o coletor de lixo atua como um gerenciador automático de memória. Ele oferece os seguintes benefícios:

* Permite que você desenvolva seu aplicativo sem a necessidade de liberar memória. 

* Aloca objetos no heap gerenciado com eficiência. 

* Recupera os objetos que não estão sendo usados, limpa a memória e mantém a memória disponível para alocações futuras. Os objetos gerenciados obtêm automaticamente conteúdo limpo com o qual começar, portanto, seus construtores não precisam inicializar cada campo de dados.

* Fornece segurança de memória, assegurando que um objeto não possa usar o conteúdo de outro objeto.


Este tópico descreve os principais conceitos da coleta de lixo. Ele contém as seguintes seções:

* [Conceitos básicos de memória](#fundamentals-of-memory)

* [Condições para uma coleta de lixo](#conditions-for-a-garbage-collection)

* [O heap gerenciado](#the-managed-heap)

* [Gerações](#generations)

* [O que acontece durante uma coleta de lixo](#what-happens-during-a-garbage-collection)

* [Manipulação de recursos não gerenciados](#manipulating-unmanaged-resources)

## <a name="fundamentals-of-memory"></a>Conceitos básicos de memória

A lista a seguir resume conceitos importantes de memória do CLR.

* Cada processo tem seu próprio espaço de endereço virtual separado. Todos os processos no mesmo computador compartilham a mesma memória física e arquivo de paginação, se houver algum.

* Por padrão, em computadores de 32 bits, cada processo tem um espaço de endereço virtual no modo de usuário de 2 GB.

* Como desenvolvedor de aplicativos, você trabalha apenas com o espaço de endereço virtual e nunca manipula a memória física diretamente. O coletor de lixo aloca e libera memória virtual para você no heap gerenciado.

* A memória virtual pode estar em três estados: 

    * Livre. O bloco de memória não tem referências a ele e está disponível para alocação.

    * Reservado. O bloco de memória está disponível para seu uso e não pode ser usado para nenhuma outra solicitação de alocação. No entanto, você não pode armazenar dados nesse bloco de memória até que ele esteja comprometido. 

    * Comprometido. O bloco de memória é atribuído para armazenamento físico.

* O espaço de endereço virtual pode ficar fragmentado. Isso significa que há blocos livres, também conhecido como furos, no espaço de endereço. Quando uma alocação de memória virtual é solicitada, o gerenciador de memória virtual precisa localizar um único bloco livre suficientemente grande para atender a essa solicitação de alocação. Mesmo que você tenha 2 GB de espaço livre, a alocação que exige 2 GB não será bem-sucedida a menos que todo esse espaço esteja em um único bloco de endereço.

* Você poderá ficar sem memória se ficar sem espaço de endereço virtual para reservar ou espaço físico para confirmar.

O arquivo de paginação é usado, mesmo se a pressão de memória física (isto é, a demanda de memória física) é baixa. Na primeira vez em que a pressão de memória física estiver alta, o sistema operacional deverá liberar espaço na memória física para armazenar dados, além de fazer o backup de alguns dos dados na memória física para o arquivo de paginação. Esses dados não são paginados até que sejam necessários, portanto, é possível encontrar paginação em situações nas quais a pressão de memória física é muito baixa.

## <a name="conditions-for-a-garbage-collection"></a>Condições para uma coleta de lixo

A coleta de lixo ocorre quando uma das seguintes condições é verdadeira:

* O sistema tem pouca memória física.

* A memória usada por objetos alocados no heap gerenciado ultrapassa o limite aceitável. Esse limite é ajustado continuamente enquanto o processo é executado.

* O método [GC.Collect](xref:System.GC.Collect) é chamado. Em quase todos os casos, você não precisa chamar esse método porque o coletor de lixo funciona continuamente. Esse método é usado principalmente para situações exclusivas e testes. 

## <a name="the-managed-heap"></a>O heap gerenciado

Depois que o coletor de lixo é inicializado pelo CLR, ele aloca um segmento da memória para armazenar e gerenciar objetos. Essa memória é chamada de heap gerenciado, em contraposição a um heap nativo no sistema operacional. 

Há um heap gerenciado para cada processo gerenciado. Todos os threads no processo alocam memória para objetos no mesmo heap.

> [!IMPORTANT]
> O tamanho de segmentos alocados pelo coletor de lixo é específico da implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas. Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento. 
 
Quanto menos objetos alocados no heap, menos trabalho o coletor de lixo precisa fazer. Ao alocar objetos, não use valores arredondados que excedam suas necessidades, por exemplo, alocando uma matriz de 32 bytes quando são necessários apenas 15 bytes. 

Quando uma coleta de lixo é disparada, o coletor de lixo recupera a memória ocupada por objetos inativos. O processo de recuperação compacta objetos vivos para que eles sejam movidos juntos e o espaço inativo é removido, tornando o heap menor. Isso garante que os objetos que são alocados juntos permaneçam juntos no heap gerenciado, para preservar sua localidade.

O grau de intrusão (frequência e a duração) de coletas de lixo é o resultado do volume de alocações e da quantidade de memória restante no heap gerenciado. 

O heap pode ser considerado como o acúmulo de dois heaps: o heap de objetos grandes e o heap de objetos pequenos. 

O heap de objetos grandes contém objetos muito grandes, com 85.000 bytes ou mais. Os objetos no heap de objetos grandes normalmente são matrizes. É raro que um objeto de instância seja muito grande. 

## <a name="generations"></a>Gerações

O heap está organizado em gerações de modo que possa manipular objetos de vida útil longa e curta. A coleta de lixo ocorre principalmente com a recuperação de objetos de vida útil curta, que geralmente ocupam apenas uma pequena parte do heap. Há três gerações de objetos no heap: 

* **Geração 0.** Essa é a geração mais jovem e contém objetos de vida útil curta. Um exemplo de um objeto de vida útil curta é uma variável temporária. A coleta de lixo ocorre com mais frequência nessa geração. 

  Objetos alocados recentemente formam uma nova geração de objetos e, implicitamente, são coletas de geração 0, a menos que sejam objetos grandes; nesse caso, entram no heap de objetos grandes em uma coleta de geração 2.

  A maioria dos objetos são recuperados para coleta de lixo na geração 0 e não sobrevivem para a próxima geração. 

* **Geração 1.** Essa geração contém objetos de vida útil curta e serve como um buffer entre objetos de vida útil curta e longa. 

* **Geração 2.** Essa geração contém objetos de vida útil longa. Um exemplo de um objeto de vida útil longa é um objeto em um aplicativo para servidores que contém dados estáticos que estão vivos durante o processo.

Coletas de lixo ocorrem em gerações específicas conforme as condições permitirem. Coletar uma geração significa coletar objetos nessa geração e todas as suas gerações mais jovens. Uma coleta de lixo da geração 2 também é conhecida como uma coleta de lixo completa, pois ela recupera todos os objetos em todas as gerações (ou seja, todos os objetos no heap gerenciado).

### <a name="survival-and-promotions"></a>Sobrevivência e promoções

Objetos que não são recuperados em uma coleta de lixo são os sobreviventes e são promovidos à próxima geração. Objetos que sobrevivem a uma coleta de lixo da geração 0 são promovidos à geração 1; objetos que sobrevivem a uma coleta de lixo da geração 1 são promovidos à geração 2 e objetos que sobrevivem a uma coleta de lixo da geração 2 permanecem na geração 2.

Quando o coletor de lixo detecta que a taxa de sobrevivência é alta em uma geração ele aumenta o limite de alocações para a geração em questão, de modo que a próxima coleta obtém um tamanho substancial de memória recuperado. O CLR equilibra continuamente duas prioridades: não permitir que o conjunto de trabalho de um aplicativo fique muito grande e não permitir que a coleta de lixo demore muito tempo.

### <a name="ephemeral-generations-and-segments"></a>Gerações e segmentos efêmeros

Devido ao fato de os objetos em gerações 0 e 1 serem de vida útil curta, essas gerações são conhecidas como as gerações efêmeras. 

As gerações efêmeras devem ser alocadas no segmento de memória que é conhecido como o segmento efêmero. Cada novo segmento adquirido pelo coletor de lixo torna-se o novo segmento efêmero e contém os objetos que sobreviveram a uma coleta de lixo da geração 0. O segmento efêmero antigo torna-se o novo segmento da geração 2. 


O segmento efêmero pode incluir objetos da geração 2. Objetos da geração 2 podem usar vários segmentos (tantos quanto exigido pelo seu processo e permitido pela memória). 

A quantidade de memória liberada de uma coleta de lixo efêmera é limitada ao tamanho do segmento efêmero. A quantidade de memória liberada é proporcional ao espaço que era ocupado pelos objetos inativos.

## <a name="what-happens-during-a-garbage-collection"></a>O que ocorre durante uma coleta de lixo

Uma coleta de lixo tem as seguintes fases: 

* Uma fase de marcação que localiza todos os objetos vivos e cria uma lista desses objetos.

* Uma fase de relocação que atualiza as referências aos objetos que serão compactados. 

* Uma fase de compactação que recupera o espaço ocupado por objetos inativos e compacta os objetos sobreviventes. A fase de compactação move objetos que sobreviveram a uma coleta de lixo em direção à extremidade mais antiga do segmento. 

Em virtude das coletas da geração 2 poderem ocupar vários segmentos, objetos que são promovidos para a geração 2 podem ser movidos para um segmento mais antigo. Tanto os sobreviventes da geração 1 quanto da geração 2 podem ser movidos para um segmento diferente, porque eles são promovidos para a geração 2. 

Normalmente o heap de objetos grandes não é compactado, porque copiar objetos grandes causa uma penalidade de desempenho. No entanto, você pode usar a propriedade [GCSettings.LargeObjectHeapCompactionMode](xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode) para compactar o heap de objetos grandes sob demanda. 

O coletor de lixo usa as informações a seguir para determinar se os objetos estão vivos: 

* **Raízes de pilha.** Variáveis de pilha fornecidas pelo compilador JIT (just-in-time) e movimentador de pilhas.

* **Identificadores de coleta de lixo.** Identificadores que apontam para objetos gerenciados e que podem ser alocados pelo código do usuário ou pelo Common Language Runtime.

* **Dados estáticos.** Objetos estáticos em domínios de aplicativo que podem fazer referência a outros objetos. Cada domínio de aplicativo controla seus objetos estáticos.

Antes de iniciar uma coleta de lixo, todos os threads gerenciados são suspensos, exceto o thread que disparou a coleta de lixo.

A ilustração a seguir mostra um thread que dispara uma coleta de lixo e faz com que outros threads sejam suspensos.

![Quando um thread dispara uma coleta de lixo](./media/fundamentals/393001.png)

Thread que dispara uma coleta de lixo

## <a name="manipulating-unmanaged-resources"></a>Manipulação de recursos não gerenciados

Se os objetos gerenciados referenciarem objetos não gerenciados por meio do uso de seus identificadores de arquivo nativo, você deverá liberar explicitamente os objetos não gerenciados, porque o coletor de lixo rastreia a memória somente no heap gerenciado.

Os usuários do seu objeto gerenciado não podem descartar os recursos nativos usados pelo objeto. Para executar a limpeza, você pode tornar o objeto gerenciado finalizável. A finalização consiste em ações de limpeza que são executadas quando o objeto não está mais em uso. Quando o objeto gerenciado é desativado, ele executa ações de limpeza que são especificadas em seu método finalizador.

Quando é descoberto que um objeto finalizável está inativo, seu finalizador é colocado em uma fila para que suas ações de limpeza sejam executadas, mas o próprio objeto é promovido para a próxima geração. Portanto, você precisa esperar até a próxima coleta de lixo ocorrer nessa geração (que não é necessariamente a próxima coleta de lixo) para determinar se o objeto foi recuperado.

## <a name="see-also"></a>Consulte também

[Coleta de lixo no .NET](gc.md)

