---
title: Definições de configuração de compilação
description: Saiba mais sobre as configurações de tempo de execução que configuram como o compilador JIT funciona para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802816"
---
# <a name="run-time-configuration-options-for-compilation"></a>Opções de configuração de tempo de execução para compilação

## <a name="tiered-compilation"></a>Compilação em camadas

- Configura se o compilador JIT usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation).
- No .NET Core 3,0 e posterior, a compilação em camadas está habilitada por padrão.
- No .NET Core 2,1 e 2,2, a compilação em camadas está desabilitada por padrão.

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | habilitado para `true`<br/>`false`-desabilitado |
| **Variável de ambiente** | `COMPlus_TieredCompilation` | habilitado para `1`<br/>`0`-desabilitado |
