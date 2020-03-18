---
title: Configurações de configuração de rosca
description: Saiba mais sobre as configurações de tempo de execução que configuram o threading para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789850"
---
# <a name="run-time-configuration-options-for-threading"></a>Opções de configuração em tempo de execução para rosca

## <a name="cpu-groups"></a>Grupos de CPU

- Configura se os threads são distribuídos automaticamente entre grupos de CPU.
- Padrão: Desabilitado ( ).`0`

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | N/D | N/D |
| **Variável de ambiente** | `COMPlus_Thread_UseAllCpuGroups` | `0`- deficientes<br/>`1`- habilitado |

## <a name="minimum-threads"></a>Roscas mínimas

- Especifica o número mínimo de threads para o pool de segmentos do trabalhador.
- Corresponde ao <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> método.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MinThreads` | Um inteiro que representa o número mínimo de threads |
| **Propriedade MSBuild** | `ThreadPoolMinThreads` | Um inteiro que representa o número mínimo de threads |
| **Variável de ambiente** | N/D | N/D |

### <a name="examples"></a>Exemplos

*arquivo runtimeconfig.json:*

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

## <a name="maximum-threads"></a>Roscas máximas

- Especifica o número máximo de threads para o pool de segmentos do trabalhador.
- Corresponde ao <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> método.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MaxThreads` | Um inteiro que representa o número máximo de threads |
| **Propriedade MSBuild** | `ThreadPoolMaxThreads` | Um inteiro que representa o número máximo de threads |
| **Variável de ambiente** | N/D | N/D |

### <a name="examples"></a>Exemplos

*arquivo runtimeconfig.json:*

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
