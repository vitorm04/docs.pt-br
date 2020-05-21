---
title: Depurando configurações de configuração de criação de perfil
description: Saiba mais sobre as configurações de tempo de execução que configuram a depuração e a criação de perfil para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761987"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Opções de configuração de tempo de execução para depuração e criação de perfil

## <a name="enable-diagnostics"></a>Habilitar diagnósticos

- Configura se o depurador, o criador de perfil e o diagnóstico EventPipe estão habilitados ou desabilitados.
- Se você omitir essa configuração, os diagnósticos serão habilitados. Isso é equivalente a definir o valor como `1` .

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Variável de ambiente** | `COMPlus_EnableDiagnostics` | `1`-habilitado<br/>`0`-desabilitado |

## <a name="enable-profiling"></a>Habilitar criação de perfil

- Configura se a criação de perfil está habilitada para o processo em execução no momento.
- Se você omitir essa configuração, a criação de perfil será desabilitada. Isso é equivalente a definir o valor como `0` .

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Variável de ambiente** | `CORECLR_ENABLE_PROFILING` | `0`-desabilitado<br/>`1`-habilitado |

## <a name="profiler-guid"></a>GUID do criador de perfil

- Especifica o GUID do criador de perfil a ser carregado no processo em execução no momento.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
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
- Se você omitir essa configuração, a gravação do mapa de desempenho será desabilitada. Isso é equivalente a definir o valor como `0` .

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Variável de ambiente** | `COMPlus_PerfMapEnabled` | `0`-desabilitado<br/>`1`-habilitado |

## <a name="perf-log-markers"></a>Marcadores de log de desempenho

- Habilita ou desabilita o sinal especificado a ser aceito e ignorado como um marcador nos logs de desempenho.
- Se você omitir essa configuração, o sinal especificado não será ignorado. Isso é equivalente a definir o valor como `0` .

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Variável de ambiente** | `COMPlus_PerfMapIgnoreSignal` | `0`-desabilitado<br/>`1`-habilitado |

> [!NOTE]
> Essa configuração será ignorada se [COMPlus_PerfMapEnabled](#write-perf-map) for omitida ou definida como `0` (ou seja, desabilitada).
