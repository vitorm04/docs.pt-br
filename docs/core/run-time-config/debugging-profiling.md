---
title: Depurando configurações de configuração de criação de perfil
description: Saiba mais sobre as configurações de tempo de execução que configuram a depuração e a criação de perfil para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802795"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Opções de configuração de tempo de execução para depuração e criação de perfil

## <a name="enable-diagnostics"></a>Habilitar diagnósticos

- Configura se o depurador, o criador de perfil e o diagnóstico EventPipe estão habilitados ou desabilitados.
- Padrão: habilitado (`1`).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `COMPlus_EnableDiagnostics` | habilitado para `1`<br/>`0`-desabilitado |

## <a name="enable-profiling"></a>Habilitar criação de perfil

- Configura se a criação de perfil está habilitada para o processo em execução no momento.
- Padrão: desabilitado (`0`).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `CORECLR_ENABLE_PROFILING` | `0`-desabilitado<br/>habilitado para `1` |

## <a name="profiler-guid"></a>GUID do criador de perfil

- Especifica o GUID do criador de perfil a ser carregado no processo em execução no momento.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `CORECLR_PROFILER` | *GUID de cadeia de caracteres* |

## <a name="profiler-location"></a>Local do criador de perfil

- Especifica o caminho para a DLL do criador de perfil a ser carregada no processo em execução no momento (ou no processo de 32 bits ou 64 bits).
- Se mais de uma variável for definida, as variáveis específicas de bit de bits têm precedência. Eles especificam qual bit de Profiler carregar.
- Para obter mais informações, consulte [localizando a biblioteca do profiler](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Nome da configuração | Valores |
| - | - | - |
| **Variável de ambiente** | `CORECLR_PROFILER_PATH` | *Cadeia de caracteres-caminho* |
| **Variável de ambiente** | `CORECLR_PROFILER_PATH_32` | *Cadeia de caracteres-caminho* |
| **Variável de ambiente** | `CORECLR_PROFILER_PATH_64` | *Cadeia de caracteres-caminho* |

## <a name="write-perf-map"></a>Gravar mapa de desempenho

- Habilita ou desabilita a gravação de */tmp/perf-$PID. map* em sistemas Linux.
- Padrão: desabilitado (`0`).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `COMPlus_PerfMapEnabled` | `0`-desabilitado<br/>habilitado para `1` |

## <a name="perf-log-markers"></a>Marcadores de log de desempenho

- Quando `COMPlus_PerfMapEnabled` é definido como `1`, habilita ou desabilita o sinal especificado a ser aceito e ignorado como um marcador nos logs de desempenho.
- Padrão: desabilitado (`0`).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `COMPlus_PerfMapIgnoreSignal` | `0`-desabilitado<br/>habilitado para `1` |
