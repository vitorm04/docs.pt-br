---
title: Estação de trabalho vs. coleta de lixo do servidor (GC)
description: Saiba mais sobre a coleta de lixo de estação de trabalho e servidor em .NET.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 6b8e5f6802e5d44669b95d43d4e897fa4a418512
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103551"
---
# <a name="workstation-and-server-garbage-collection"></a>Coleta de lixo de estação de trabalho ou de servidor

O coletor de lixo tem autoajuste e pode trabalhar em uma ampla variedade de cenários. No entanto, você pode [definir o tipo de coleta de lixo](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) com base nas características da carga de trabalho. O CLR fornece os seguintes tipos de coleta de lixo:

- Coleta de lixo de estação de trabalho (GC), que é projetada para aplicativos de clientes. É o sabor GC padrão para aplicativos autônomos. Para aplicativos hospedados, por exemplo, aqueles hospedados por ASP.NET, o host determina o sabor GC padrão.

  A coleta de lixo da estação de trabalho pode ser simultânea ou não simultânea. A coleta simultânea (ou *de fundo)* permite que os fios gerenciados continuem as operações durante uma coleta de lixo. [A coleta de lixo em segundo plano](background-gc.md) substitui a coleta de lixo [simultânea](background-gc.md#concurrent-garbage-collection) nas versões .NET Framework 4 e posteriores.

- A coleta de lixo de servidor, que serve para aplicativos de servidor que precisam de escalabilidade e taxa de transferência altas.

  - No .NET Core, a coleta de lixo do servidor pode ser não simultânea ou em segundo plano.

  - Nas versões .NET Framework 4.5 e posteriores, a coleta de lixo do servidor pode ser não simultânea ou em segundo plano. No Framework 4 e nas versões anteriores, a coleta de lixo do servidor não é simultânea.

A ilustração a seguir mostra os tópicos dedicados que realizam a coleta de lixo em um servidor:

![Threads de coleta de lixo do servidor](./media/gc-server.png)

## <a name="performance-considerations"></a>Considerações sobre o desempenho

### <a name="workstation-gc"></a>GC da estação de trabalho

Veja a seguir considerações de desempenho e de threading para a coleta de lixo da estação de trabalho:

- A coleção ocorre no thread do usuário que disparou a coleta de lixo e permanece com a mesma prioridade. Como os threads de usuário normalmente são executados com prioridade normal, o coletor de lixo (que é executado em um thread de prioridade normal) deve disputam competir outros threads por tempo da CPU. (Os threads que executam código nativo não estão suspensos em nenhuma coleta de lixo do servidor ou da estação de trabalho.)

- A coleta de lixo da estação de trabalho é sempre usada em um computador que tem apenas um processador, independentemente da [configuração de configuração](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

### <a name="server-gc"></a>GC do servidor

Veja a seguir considerações de desempenho e de threading para a coleta de lixo de servidor:

- A coleta ocorre em vários threads dedicados que estão em execução no nível de prioridade `THREAD_PRIORITY_HIGHEST`.

- Fornece-se um heap e um thread dedicado para executar a coleta de lixo para cada CPU, e os heaps são coletados ao mesmo tempo. Cada heap contém um heap de objeto pequeno e um heap de objeto grande, e todos os heaps podem ser acessados pelo código do usuário. Objetos em heaps diferentes podem fazer referência entre si.

- Como vários threads de coleta de lixo funcionam em conjunto, a coleta de lixo de servidor é mais rápida do que a coleta de lixo de estação de trabalho no heap de mesmo tamanho.

- Geralmente, a coleta de lixo de servidor tem segmentos maiores. No entanto, trata-se apenas de uma generalização: o tamanho do segmento é específico da implementação e está sujeito a alterações. Não faça suposições sobre o tamanho dos segmentos alocados pelo coletor de lixo ao sintonizar seu aplicativo.

- A coleta de lixo de servidor pode usar bastante recursos. Por exemplo, imagine que existem 12 processos que usam o servidor GC em execução em um computador que tem quatro processadores. Se todos os processos acontecerem de coletar lixo ao mesmo tempo, eles interfeririam uns com os outros, pois haveria 12 threads programados no mesmo processador. Se os processos estão ativos, não é uma boa idéia tê-los todos usando o servidor GC.

Se você está executando centenas de instâncias de um aplicativo, considere usar a coleta de lixo da estação de trabalho com coleta de lixo simultânea desativada. Isso resultará na redução da comutação de contexto, o que pode melhorar o desempenho.

## <a name="see-also"></a>Confira também

- [Coleta de lixo de fundo](background-gc.md)
- [Opções de configuração em tempo de execução para coleta de lixo](../../core/run-time-config/garbage-collector.md)
