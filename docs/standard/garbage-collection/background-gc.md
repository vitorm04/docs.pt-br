---
title: Coleta de lixo de fundo
description: Saiba mais sobre a coleta de lixo em plano .NET e como ela difere na coleta de lixo de estações de trabalho e servidores.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: dcb1d348e679e07646273b8fbc4ea29b44ee4974
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103558"
---
# <a name="background-garbage-collection"></a>Coleta de lixo de fundo

Na coleta de lixo de fundo (GC), as gerações efêmeras (0 e 1) são coletadas conforme necessário enquanto a coleta da geração 2 está em andamento. A coleta de lixo em segundo plano é realizada em um ou mais threads dedicados, dependendo se é de fundo ou gc servidor, e se aplica apenas às coleções de geração 2.

A coleta de lixo de fundo é habilitada por padrão. Ele pode ser ativado ou desativado com a configuração [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) em aplicativos .NET Framework ou na configuração [System.GC.Simultâneo](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) em aplicativos .NET Core.

> [!NOTE]
> A coleta de lixo em segundo plano substitui [a coleta de lixo simultânea](#concurrent-garbage-collection) e está disponível nas versões .NET Framework 4 e posteriores. No Quadro .NET 4, ele é suportado apenas para coleta de lixo *de estações de trabalho.* A partir do .NET Framework 4.5, a coleta de lixo em segundo plano está disponível tanto para a coleta de lixo *da estação de trabalho* quanto para o *servidor.*

Uma coleta de gerações efêmeras durante a coleta de lixo de fundo é conhecida como coleta de lixo *em primeiro plano.* Quando as coletas de lixo em primeiro plano ocorrem, todos os threads gerenciados são suspensos.

Quando a coleta de lixo de fundo está em andamento e você alocou objetos suficientes na geração 0, a CLR realiza uma coleta de lixo de geração 0 ou geração 1 em primeiro plano. O thread dedicado de coleta de lixo em segundo plano verifica em pontos frequentes de segurança se há uma solicitação de coleta de lixo em primeiro plano. Se houver, a coleta de plano de fundo suspende a si mesma para que a coleta de lixo em primeiro plano possa ocorrer. Depois que a coleta de lixo em primeiro plano é concluída, os segmentos dedicados de coleta de lixo de fundo e os threads do usuário são retomados.

A coleta de lixo em segundo plano remove as restrições de alocação impostas pela coleta de lixo simultânea, pois as coletas de lixo efêmeras podem ocorrer durante a coleta de lixo em segundo plano. A coleta de lixo de fundo pode remover objetos mortos em gerações efêmeras. Também pode expandir o monte se necessário durante uma coleta de lixo de geração 1.

## <a name="background-workstation-vs-server-gc"></a>Estação de trabalho de fundo vs. servidor GC

A partir do .NET Framework 4.5, a coleta de lixo em segundo plano está disponível para o servidor GC. Background GC é o modo padrão para coleta de lixo do servidor.

A coleta de lixo do servidor em segundo plano funciona de forma semelhante à coleta de lixo em segundo plano, mas há algumas diferenças:

- A coleta de lixo de base da estação de trabalho usa um segmento dedicado de coleta de lixo em segundo plano, enquanto a coleta de lixo do servidor em segundo plano usa vários threads. Normalmente, há um segmento dedicado para cada processador lógico.

- Ao contrário do segmento de coleta de lixo em segundo plano da estação de trabalho, os threads GC do servidor de fundo não têm tempo.

A ilustração a seguir mostra a coleta de lixo *da estação de trabalho* em segundo plano realizada em um segmento separado e dedicado:

![Coleta de lixo de estação de trabalho em segundo plano](./media/fundamentals/background-workstation-garbage-collection.png)

A ilustração a seguir mostra a coleta de lixo do *servidor* em plano de fundo realizada em threads separados e dedicados:

![Coleta de lixo de servidor em segundo plano](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Coleta de lixo simultânea

> [!TIP]
> Esta seção aplica-se a:
>
> - .NET Framework 3.5 e anteriormente para coleta de lixo de estação de trabalho
> - .NET Framework 4 e anteriorpara coleta de lixo do servidor
>
> O lixo simultâneo é substituído pela coleta de lixo de fundo em versões posteriores.

Na coleta de lixo de estação de trabalho ou servidor, você pode [habilitar a coleta simultânea](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)de lixo, o que permite que os threads funcionem simultaneamente com um segmento dedicado que realiza a coleta de lixo durante a maior parte da duração da coleta. Essa opção afeta apenas as coletas de lixo na geração 2; gerações 0 e 1 são sempre não simultâneas porque terminam rápido.

A coleta de lixo simultânea permite que aplicativos interativos sejam mais responsivos minimizando a pausa para uma coleta. Na maioria das vezes, a execução dos threads gerenciados pode continuar enquanto o thread de coleta de lixo simultânea estiver em execução. Isso resulta em pausas menores enquanto uma coleta de lixo estiver em execução.

A coleta de lixo simultânea é executada em um thread dedicado. Por padrão, a CLR executa a coleta de lixo da estação de trabalho com coleta de lixo simultânea ativada em computadores de processador único e vários processadores.

A ilustração a seguir mostra a coleta de lixo simultânea executada em um thread dedicado separado.

![Fios de coleta de lixo simultâneos](./media/gc-concurrent.png)

## <a name="see-also"></a>Confira também

- [Coleta de lixo de estação de trabalho ou de servidor](workstation-server-gc.md)
- [Opções de configuração em tempo de execução para coleta de lixo](../../core/run-time-config/garbage-collector.md)
