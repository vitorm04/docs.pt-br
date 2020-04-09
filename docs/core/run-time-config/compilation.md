---
title: Configurações de configuração de compilação
description: Saiba mais sobre as configurações de tempo de execução que configuram como o compilador JIT funciona para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ac51aa13254b2f2b1fdd8d1dd9c52559831a1659
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989110"
---
# <a name="run-time-configuration-options-for-compilation"></a>Opções de configuração em tempo de execução para compilação

## <a name="tiered-compilation"></a>Compilação em camadas

- Configura se o compilador just-in-time (JIT) usa [compilação hierárquica](../whats-new/dotnet-core-3-0.md#tiered-compilation). Métodos de transição de compilação hierárquico através de dois níveis:
  - O primeiro nível gera código mais rapidamente[(JIT rápido)](#quick-jit)ou carrega código pré-compilado[(ReadyToRun).](#readytorun)
  - O segundo nível gera código otimizado em segundo plano ("otimizando o JIT").
- No .NET Core 3.0 e posterior, a compilação hierárquica é habilitada por padrão.
- No .NET Core 2.1 e 2.2, a compilação hierárquica é desativada por padrão.
- Para obter mais informações, consulte o [guia de compilação hierárquico](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation` | `true`- habilitado<br/>`false`- deficientes |
| **Propriedade MSBuild** | `TieredCompilation` | `true`- habilitado<br/>`false`- deficientes |
| **Variável de ambiente** | `COMPlus_TieredCompilation` | `1`- habilitado<br/>`0`- deficientes |

### <a name="examples"></a>Exemplos

*arquivo runtimeconfig.json:*

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

## <a name="quick-jit"></a>JIT Rápido

- Configura se o compilador JIT usa *JIT rápido*. Para métodos que não contêm loops e para os quais o código pré-compilado não está disponível, o JIT rápido os compila mais rapidamente, mas sem otimizações.
- Permitir jit rápido diminui o tempo de inicialização, mas pode produzir código com características de desempenho degradadas. Por exemplo, o código pode usar mais espaço de pilha, alocar mais memória e executar mais devagar.
- Se o JIT rápido estiver desativado, mas [a compilação hierárquica](#tiered-compilation) estiver ativada, apenas o código pré-compilado participará da compilação hierárquica. Se um método não for pré-compilado com [ReadyToRun,](#readytorun)o comportamento do JIT é o mesmo que se a [compilação hierárquica](#tiered-compilation) fosse desativada.
- No .NET Core 3.0 e posterior, o JIT rápido é habilitado por padrão.
- No .NET Core 2.1 e 2.2, o JIT rápido é desativado por padrão.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJit` | `true`- habilitado<br/>`false`- deficientes |
| **Propriedade MSBuild** | `TieredCompilationQuickJit` | `true`- habilitado<br/>`false`- deficientes |
| **Variável de ambiente** | `COMPlus_TC_QuickJit` | `1`- habilitado<br/>`0`- deficientes |

### <a name="examples"></a>Exemplos

*arquivo runtimeconfig.json:*

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

- Configura se o compilador JIT usa JIT rápido em métodos que contêm loops.
- A habilitação de JIT rápido para loops pode melhorar o desempenho da inicialização. No entanto, loops de longa duração podem ficar presos em códigos menos otimizados por longos períodos.
- Se [o JIT rápido](#quick-jit) estiver desativado, esta configuração não tem efeito.
- Padrão: Desabilitado ( ).`false`

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`- deficientes<br/>`true`- habilitado |
| **Propriedade MSBuild** | `TieredCompilationQuickJitForLoops` | `false`- deficientes<br/>`true`- habilitado |
| **Variável de ambiente** | `COMPlus_TC_QuickJitForLoops` | `0`- deficientes<br/>`1`- habilitado |

### <a name="examples"></a>Exemplos

*arquivo runtimeconfig.json:*

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
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>ReadyToRun

- Configura se o tempo de execução do .NET Core usa código pré-compilado para imagens com dados ReadyToRun disponíveis. Desativar essa opção força o tempo de execução para o código de estrutura jit-compilar.
- Para obter mais informações, consulte [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).
- Padrão: Ativado`1`().

| | Nome da configuração | Valores |
| - | - | - |
| **Variável de ambiente** | `COMPlus_ReadyToRun` | `1`- habilitado<br/>`0`- deficientes |
