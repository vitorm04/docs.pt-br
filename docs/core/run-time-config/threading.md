---
title: Definições de configuração de Threading
description: Saiba mais sobre as configurações de tempo de execução que configuram Threading para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802760"
---
# <a name="run-time-configuration-options-for-threading"></a>Opções de configuração de tempo de execução para Threading

## <a name="cpu-groups"></a>Grupos de CPU

- Define se os threads são distribuídos automaticamente entre grupos de CPU.
- Padrão: desabilitado (`0`).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `COMPlus_Thread_UseAllCpuGroups` | `0`-desabilitado<br/>habilitado para `1` |

## <a name="minimum-threads"></a>Mínimo de threads

- Especifica o número mínimo de threads para o ThreadPool de trabalho.
- Corresponde ao método de <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | Um inteiro que representa o número mínimo de threads |
| **Variável de ambiente** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |

## <a name="maximum-threads"></a>Máximo de threads

- Especifica o número máximo de threads para o ThreadPool de trabalho.
- Corresponde ao método de <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Um inteiro que representa o número máximo de threads |
| **Variável de ambiente** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
