---
title: Modos de latência
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: a8eaf0c80aa32978eead80c51a905cbcd66a537b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283591"
---
# <a name="latency-modes"></a>Modos de latência

Para recuperar objetos, o coletor de lixo (GC) deve parar todos os segmentos de execução em uma aplicação. O período durante o qual o coletor de lixo está ativo é referido como sua *latência.*

Em algumas situações, como quando um aplicativo recupera dados ou exibe conteúdo, uma coleta de lixo completa pode ocorrer em um momento crítico e impedir o desempenho. Você pode ajustar a intrusão do coletor de lixo, definindo a propriedade <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> como um dos valores <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>.

## <a name="low-latency-settings"></a>Configurações de baixa latência

Usar uma configuração de latência "baixa" significa que o coletor de lixo se intromete menos em sua aplicação. A coleta de lixo é mais conservadora sobre recuperar a memória.

A enumeração <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> fornece duas configurações de baixa latência:

- [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) suprime coleções de geração 2 e realiza apenas coleções de geração 0 e 1. Ela pode ser usada somente por curtos períodos. Em períodos mais longos, se o sistema estiver sob pressão de memória, o coletor de lixo disparará uma coleção, que pode pausar o aplicativo rapidamente e interromper uma operação de tempo crítico. Essa configuração está disponível somente para coleta de lixo de estação de trabalho.

- [GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) suprime coleções de geração em primeiro plano 2 e executa apenas coleções de geração 0, 1 e geração de fundo 2. Ela pode ser usada por longos períodos e está disponível para coleta de lixo de estação de trabalho e servidor. Esta configuração não pode ser usada se a coleta de lixo de fundo estiver desativada.

Durante períodos de baixa latência, coletas da geração 2 são suprimidas, a menos que ocorra o seguinte:

- O sistema recebe uma notificação de falta de memória do sistema operacional.

- O código do aplicativo induz uma coleta chamando o <xref:System.GC.Collect%2A?displayProperty=nameWithType> método e especificando 2 para o `generation` parâmetro.

## <a name="scenarios"></a>Cenários

A tabela a seguir lista <xref:System.Runtime.GCLatencyMode> os cenários do aplicativo para usar os valores:

|Modo de latência|Cenários de aplicativos|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|Para aplicativos que não possuem interface de usuário (Interface do Usuário) ou operações do lado do servidor.<br /><br />Quando a coleta de lixo em segundo plano é desativada, este é o modo padrão para a coleta de lixo da estação de trabalho e do servidor. <xref:System.Runtime.GCLatencyMode.Batch>o modo também substitui a configuração [gcConcurrent,](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) ou seja, impede coleções de fundo ou simultâneas.|
|<xref:System.Runtime.GCLatencyMode.Interactive>|Para a maioria dos aplicativos que têm uma interface do usuário.<br /><br />Este é o modo padrão para a coleta de lixo da estação de trabalho e do servidor. No entanto, se um aplicativo estiver hospedado, as configurações de coletor de lixo do processo de hospedagem terão precedência.|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Para aplicativos que têm operações de curto prazo, sensíveis ao tempo, durante o qual as interrupções do coletor de lixo podem ser prejudiciais. Por exemplo, aplicativos que renderizam animações ou funções de aquisição de dados.|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Para aplicativos que têm operações sensíveis ao tempo, por uma duração contida, mas potencialmente maior, durante a qual as interrupções do coletor de lixo poderiam ser prejudiciais. Por exemplo, aplicativos que precisam de tempos de resposta rápidos, como alterações de dados de mercado durante o horário comercial.<br /><br />Esse modo resulta em um tamanho maior do heap gerenciado do que outros modos. Como ele não compacta o heap gerenciado, é possível maior fragmentação. Verifique se há memória suficiente disponível.|

## <a name="guidelines-for-using-low-latency"></a>Diretrizes para o uso de baixa latência

Ao usar o modo [GCLatencyMode.LowLatency,](xref:System.Runtime.GCLatencyMode.LowLatency) considere as seguintes diretrizes:

- Mantenha o período de baixa latência o mais curto possível.

- Evite a alocação de grande quantidade de memória durante períodos de baixa latência. Notificações de memória insuficiente podem ocorrer porque a coleta de lixo recupera menos objetos.

- Enquanto estiver no modo de baixa latência, minimize o número de novas alocações, em particular alocações no grande monte de objetos e objetos fixos.

- Esteja atento a ameaças que possam ser alocadas. Como <xref:System.Runtime.GCSettings.LatencyMode%2A> a configuração de <xref:System.OutOfMemoryException> propriedade é em todo o processo, exceções podem ser geradas em qualquer segmento que esteja alocando.

- Enrole o código de baixa latência em regiões de execução restritas. Para obter mais informações, consulte [regiões de execução restritas](../../../docs/framework/performance/constrained-execution-regions.md).

- Você pode forçar coletas da geração 2 durante um período de baixa latência ao chamar o método <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType>.

## <a name="see-also"></a>Confira também

- <xref:System.GC?displayProperty=nameWithType>
- [Coletas Induzidas](../../../docs/standard/garbage-collection/induced.md)
- [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
