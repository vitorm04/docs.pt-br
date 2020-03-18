---
title: Depuração configurações de configuração de configuração de perfil
description: Saiba mais sobre as configurações de tempo de execução que configuram a depuração e o perfil dos aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802795"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Opções de configuração em tempo de execução para depuração e criação de perfil

## <a name="enable-diagnostics"></a>Habilitar diagnósticos

- Configura se o depurador, o profiler e o diagnóstico EventPipe estão ativados ou desativados.
- Padrão: Ativado`1`().

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | N/D | N/D |
| **Variável de ambiente** | `COMPlus_EnableDiagnostics` | `1`- habilitado<br/>`0`- deficientes |

## <a name="enable-profiling"></a>Habilitar criação de perfil

- Configura se o perfil está ativado para o processo em execução no momento.
- Padrão: Desabilitado ( ).`0`

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | N/D | N/D |
| **Variável de ambiente** | `CORECLR_ENABLE_PROFILING` | `0`- deficientes<br/>`1`- habilitado |

## <a name="profiler-guid"></a>GUIA DO Profiler

- Especifica o GUID do profiler para carregar no processo em execução no momento.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | N/D | N/D |
| **Variável de ambiente** | `CORECLR_PROFILER` | *string-guid* |

## <a name="profiler-location"></a>Localização do profiler

- Especifica o caminho para o dLL do profiler para carregar no processo em execução atual (ou processo de 32 bits ou 64 bits).
- Se mais de uma variável for definida, as variáveis específicas da bitness têm precedência. Eles especificam qual bitness do profiler carregar.
- Para obter mais informações, consulte [Encontrar a biblioteca profiler](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Nome da configuração | Valores |
| - | - | - |
| **Variável de ambiente** | `CORECLR_PROFILER_PATH` | *string-path* |
| **Variável de ambiente** | `CORECLR_PROFILER_PATH_32` | *string-path* |
| **Variável de ambiente** | `CORECLR_PROFILER_PATH_64` | *string-path* |

## <a name="write-perf-map"></a>Escrever mapa perf

- Ativa ou desativa a escrita */tmp/perf-$pid.map* nos sistemas Linux.
- Padrão: Desabilitado ( ).`0`

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | N/D | N/D |
| **Variável de ambiente** | `COMPlus_PerfMapEnabled` | `0`- deficientes<br/>`1`- habilitado |

## <a name="perf-log-markers"></a>Marcadores de log perf

- Quando `COMPlus_PerfMapEnabled` estiver `1`definido para , habilita ou desativa o sinal especificado a ser aceito e ignorado como um marcador nos logs perf.
- Padrão: Desabilitado ( ).`0`

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | N/D | N/D |
| **Variável de ambiente** | `COMPlus_PerfMapIgnoreSignal` | `0`- deficientes<br/>`1`- habilitado |
