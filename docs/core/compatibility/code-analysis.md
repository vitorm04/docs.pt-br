---
title: Alterações significativas na análise de código
description: Lista as alterações significativas nos analisadores de código-fonte do .NET.
ms.date: 09/02/2020
ms.openlocfilehash: 3cbe2ecf5d08084db542db0c2da016f1f391452e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538911"
---
# <a name="code-analysis-breaking-changes"></a>Alterações significativas na análise de código

As seguintes alterações significativas estão documentadas nesta página:

| Alteração significativa | Versão introduzida |
| - | :-: |
| [CA1416: compatibilidade de plataforma](#ca1416-platform-compatibility) | 5,0 |
| [CA1417: OutAttribute no parâmetro de cadeia de caracteres para P/Invoke](#ca1417-outattribute-on-string-parameter-for-pinvoke) | 5,0 |
| [CA1831: usar asspan em vez de indexadores baseados em intervalo para cadeia de caracteres](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | 5,0 |
| [CA2013: Não usar ReferenceEquals com tipos de valor](#ca2013-do-not-use-referenceequals-with-value-types) | 5,0 |
| [CA2014: Não usar stackalloc em loops](#ca2014-do-not-use-stackalloc-in-loops) | 5,0 |
| [CA2015: não definir finalizadores para tipos derivados de MemoryManager\<T>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | 5,0 |
| [CA2200: Relançar para preservar detalhes da pilha](#ca2200-rethrow-to-preserve-stack-details) | 5,0 |
| [CA2247: o argumento para o Construtor TaskCompletionSource deve ser um valor TaskCreationOptions](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | 5,0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [ca1416-platform-compatibility-analyzer](../../../includes/core-changes/codeanalysis/5.0/ca1416-platform-compatibility-analyzer.md)]

***

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/ca1417-outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/ca1831-range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/ca2013-referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/ca2014-stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/ca2015-finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ca2200-rethrow-to-preserve-stack-details](../../../includes/core-changes/codeanalysis/5.0/ca2200-rethrow-to-preserve-stack-details.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ca2247-ctor-arg-should-be-taskcreationoptions.md)]

***
