---
title: Definições de configuração de Threading
description: Saiba mais sobre as configurações de tempo de execução que configuram Threading para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761922"
---
# <a name="run-time-configuration-options-for-threading"></a>Opções de configuração de tempo de execução para Threading

## <a name="cpu-groups"></a>Grupos de CPU

- Define se os threads são distribuídos automaticamente entre grupos de CPU.
- Se você omitir essa configuração, os threads não serão distribuídos em grupos de CPU. Isso é equivalente a definir o valor como `0` .

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | N/D | N/D |
| **Variável de ambiente** | `COMPlus_Thread_UseAllCpuGroups` | `0`-desabilitado<br/>`1`-habilitado |

## <a name="minimum-threads"></a>Mínimo de threads

- Especifica o número mínimo de threads para o pool de threads de trabalho.
- Corresponde ao <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> método.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | Um inteiro que representa o número mínimo de threads |
| **Propriedade do MSBuild** | `ThreadPoolMinThreads` | Um inteiro que representa o número mínimo de threads |
| **Variável de ambiente** | N/D | N/D |

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

- Especifica o número máximo de threads para o pool de threads de trabalho.
- Corresponde ao <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> método.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Um inteiro que representa o número máximo de threads |
| **Propriedade do MSBuild** | `ThreadPoolMaxThreads` | Um inteiro que representa o número máximo de threads |
| **Variável de ambiente** | N/D | N/D |

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
