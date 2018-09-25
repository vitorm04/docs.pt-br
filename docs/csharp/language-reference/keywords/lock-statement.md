---
title: Instrução lock (referência em C#)
description: Use a instrução lock C# para sincronizar o acesso de thread com o recurso compartilhado
ms.date: 08/28/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2b6fbfb2f81d7745c4effb9ea0087f34cc872a6c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858350"
---
# <a name="lock-statement-c-reference"></a>Instrução lock (referência em C#)

A instrução `lock` obtém o bloqueio de exclusão mútua para um determinado objeto, executa um bloco de instruções, em seguida, libera o bloqueio. Embora um bloqueio seja mantido, o thread que mantém o bloqueio pode obtê-lo novamente e liberá-lo. Qualquer outro thread é impedido de obter o bloqueio e aguarda até que ele seja liberado.

A instrução `lock` está no formato

```csharp
lock (x)
{
    // Your code...
}
```

em que `x` é uma expressão de um [tipo de referência](reference-types.md). Ela é precisamente equivalente a

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

Como o código usa um bloco [try...finally](try-finally.md), o bloqueio será liberado mesmo se uma exceção for gerada dentro do corpo de uma instrução `lock`.

Não é possível usar a palavra-chave [await](await.md) no corpo de uma instrução `lock`.

## <a name="remarks"></a>Comentários

Quando você sincroniza o acesso de thread com o recurso compartilhado, bloqueie uma instância de objeto dedicada (por exemplo, `private readonly object balanceLock = new object();`) ou outra instância que provavelmente não será usada como um objeto de bloqueio por partes não relacionadas do código. Evite usar a mesma instância de objeto de bloqueio para diferentes recursos compartilhados, uma vez que ela poderia resultar em deadlock ou contenção de bloqueio. Em particular, evite usar

- `this` (pode ser usado pelos chamadores como um bloqueio),
- <xref:System.Type> instâncias (podem ser obtidas por meio do operador ou reflexão [typeof](typeof.md)),
- instâncias de cadeia de caracteres, incluindo literais de cadeia de caracteres,

como objetos de bloqueio.

## <a name="example"></a>Exemplo

O exemplo a seguir define uma classe `Account` que sincroniza o acesso com seu campo privado `balance` bloqueando uma instância `balanceLock` dedicada. Usar a mesma instância para bloquear garante que o campo `balance` não pode ser atualizado simultaneamente por dois threads que tentam chamar os métodos `Debit` ou `Credit` simultaneamente.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Referência de C#](../index.md)
- [Palavras-chave do C#](index.md)
- [Palavras-chave de instrução](statement-keywords.md)
- [Operações interconectadas](../../../standard/threading/interlocked-operations.md)
- [Visão geral dos primitivos de sincronização](../../../standard/threading/overview-of-synchronization-primitives.md)