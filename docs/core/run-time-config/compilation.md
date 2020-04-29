---
title: Definições de configuração de compilação
description: Saiba mais sobre as configurações de tempo de execução que configuram como o compilador JIT funciona para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 4db20ee6d36fe3d3d66f473644b70c02d4e02cb3
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506838"
---
# <a name="run-time-configuration-options-for-compilation"></a>Opções de configuração de tempo de execução para compilação

## <a name="tiered-compilation"></a>Compilação em camadas

- Configura se o compilador JIT (just-in-time) usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation). A compilação em camadas faz a transição de métodos por meio de duas camadas:
  - A primeira camada gera código mais rapidamente ([JIT rápido](#quick-jit)) ou carrega código pré-compilado ([ReadyToRun](#readytorun)).
  - A segunda camada gera código otimizado em segundo plano ("Otimizando JIT").
- No .NET Core 3,0 e posterior, a compilação em camadas está habilitada por padrão.
- No .NET Core 2,1 e 2,2, a compilação em camadas está desabilitada por padrão.
- Para obter mais informações, consulte o [Guia de compilação em camadas](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | `true`-habilitado<br/>`false`-desabilitado |
| **Propriedade do MSBuild** | `TieredCompilation` | `true`-habilitado<br/>`false`-desabilitado |
| **Variável de ambiente** | `COMPlus_TieredCompilation` | `1`-habilitado<br/>`0`-desabilitado |

### <a name="examples"></a>Exemplos

arquivo *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

Arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a>JIT rápido

- Configura se o compilador JIT usa o *JIT rápido*. Para métodos que não contêm loops e para os quais o código pré-compilado não está disponível, o JIT rápido compila-os mais rapidamente, mas sem otimizações.
- Habilitar o JIT rápido diminui o tempo de inicialização, mas pode produzir código com características de desempenho degradadas. Por exemplo, o código pode usar mais espaço de pilha, alocar mais memória e executar mais lentamente.
- Se o JIT rápido estiver desabilitado, mas a [compilação em camadas](#tiered-compilation) estiver habilitada, somente o código pré-compilado participará da compilação em camadas. Se um método não for compilado previamente com [ReadyToRun](#readytorun), o comportamento de JIT será o mesmo que se a [compilação em camadas](#tiered-compilation) fosse desabilitada.
- No .NET Core 3,0 e posterior, o Quick JIT é habilitado por padrão.
- No .NET Core 2,1 e 2,2, o Quick JIT é desabilitado por padrão.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJit` | `true`-habilitado<br/>`false`-desabilitado |
| **Propriedade do MSBuild** | `TieredCompilationQuickJit` | `true`-habilitado<br/>`false`-desabilitado |
| **Variável de ambiente** | `COMPlus_TC_QuickJit` | `1`-habilitado<br/>`0`-desabilitado |

### <a name="examples"></a>Exemplos

arquivo *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

Arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a>JIT rápido para loops

- Configura se o compilador JIT usa o JIT rápido em métodos que contêm loops.
- Habilitar o JIT rápido para loops pode melhorar o desempenho de inicialização. No entanto, loops de longa execução podem ficar presos em código menos otimizado por longos períodos.
- Se a opção [JIT rápida](#quick-jit) estiver desabilitada, essa configuração não terá efeito.
- Padrão: desabilitado`false`().

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`-desabilitado<br/>`true`-habilitado |
| **Propriedade do MSBuild** | `TieredCompilationQuickJitForLoops` | `false`-desabilitado<br/>`true`-habilitado |
| **Variável de ambiente** | `COMPlus_TC_QuickJitForLoops` | `0`-desabilitado<br/>`1`-habilitado |

### <a name="examples"></a>Exemplos

arquivo *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

Arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>ReadyToRun

- Configura se o tempo de execução do .NET Core usa código pré-compilado para imagens com dados ReadyToRun disponíveis. Desabilitar essa opção força o tempo de execução para o código de estrutura JIT-compile.
- Para obter mais informações, consulte [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).
- Padrão: habilitado (`1`).

| | Nome da configuração | Valores |
| - | - | - |
| **Variável de ambiente** | `COMPlus_ReadyToRun` | `1`-habilitado<br/>`0`-desabilitado |
