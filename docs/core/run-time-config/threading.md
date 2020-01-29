---
title: Definições de configuração de Threading
description: Saiba mais sobre as configurações de tempo de execução que configuram Threading para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ed7688d4d8f7178440fe59afc6e2f5e0a11b2a5c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733426"
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
| **Propriedade do MSBuild** | `ThreadPoolMinThreads` | Um inteiro que representa o número mínimo de threads |
| **Variável de ambiente** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |

### <a name="examples"></a>Exemplos

arquivo *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

Arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a>Máximo de threads

- Especifica o número máximo de threads para o ThreadPool de trabalho.
- Corresponde ao método de <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Um inteiro que representa o número máximo de threads |
| **Propriedade do MSBuild** | `ThreadPoolMaxThreads` | Um inteiro que representa o número máximo de threads |
| **Variável de ambiente** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |

### <a name="examples"></a>Exemplos

arquivo *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

Arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
