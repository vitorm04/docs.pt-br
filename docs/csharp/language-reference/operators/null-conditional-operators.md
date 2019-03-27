---
title: Operadores nulos condicionais – referência do C#
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 9cbf8a0f860f0bc0328cd98e558b20b5e8e1bf8f
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348837"
---
# <a name="-and--null-conditional-operators-c-reference"></a>?. Operadores nulos condicionais and ?[] (referência do C#)

Testa o valor do operando esquerdo para nulo antes de executar um acesso de membro (`?.`) ou uma operação de índice (`?[]`); retorna `null` se o operando esquerdo é avaliado como `null`.

Esses operadores ajudam a escrever menos código para lidar com verificações de nulidade, especialmente para entrar em estruturas de dados.

```csharp
int? length = customers?.Length; // null if customers is null
Customer first = customers?[0];  // null if customers is null
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null
```

Os operadores condicionais nulos estão entrando em curto-circuito.  Se uma operação em uma cadeia de operações de índice e acesso de membro condicionais retornar nulo, o restante da execução da cadeia será interrompido.  No exemplo a seguir, `E` não será executado se `A`, `B` ou `C` for avaliado como nulo.

```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

Outro uso para o acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.  A maneira antiga requer código semelhante ao seguinte:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
    handler(…);
```

A nova maneira é muito mais simples:

```csharp
PropertyChanged?.Invoke(…)
```

A nova forma é thread-safe porque o compilador gera código para avaliar `PropertyChanged` somente uma vez, mantendo o resultado em uma variável temporária. Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `PropertyChanged?(e)`.

## <a name="language-specifications"></a>Especificações da linguagem

Para saber mais, confira [Operador condicional nulo](~/_csharplang/spec/expressions.md#null-conditional-operator) na [Especificação da linguagem C#](../language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.

## <a name="see-also"></a>Consulte também

- [?? (operador de união nula)](null-coalescing-operator.md)
- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)