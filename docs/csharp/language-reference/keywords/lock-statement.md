---
title: Instrução lock (referência em C#)
description: 'A palavra-chave lock é usada em threading '
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6ed46837482642dfd7e1a96cd120fc18023c5e9f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931187"
---
# <a name="lock-statement-c-reference"></a>Instrução lock (referência em C#)

A palavra-chave `lock` marca um bloco de instruções como uma seção crítica obtendo o bloqueio de exclusão mútua para um determinado objeto, executando uma instrução e, em seguida, liberando o bloqueio. O exemplo a seguir inclui uma instrução `lock`.

```csharp
class Account
{
    decimal balance;
    private Object thisLock = new Object();

    public void Withdraw(decimal amount)
    {
        lock (thisLock)
        {
            if (amount > balance)
            {
                throw new Exception("Insufficient funds");
            }
            balance -= amount;
        }
    }
}
```

Para obter mais informações, consulte [Sincronização de thread](../../programming-guide/concepts/threading/thread-synchronization.md).

## <a name="remarks"></a>Comentários

A palavra-chave `lock` garante que um thread não insere uma seção crítica do código enquanto outro thread está na seção crítica. Se outro thread tentar inserir um código bloqueado, ele aguardará, bloqueado, até que o objeto seja liberado.

A seção [Threading](../../programming-guide/concepts/threading/index.md) discute o threading.

A palavra-chave `lock` chama <xref:System.Threading.Monitor.Enter%2A> no início do bloco e <xref:System.Threading.Monitor.Exit%2A> no fim do bloco. Uma <xref:System.Threading.ThreadInterruptedException> será gerada se <xref:System.Threading.Thread.Interrupt%2A> interromper um thread que está esperando para inserir uma instrução `lock`.

Em geral, evite o bloqueio em um tipo `public` ou instâncias além do controle do código. Os constructos comuns `lock (this)`, `lock (typeof (MyType))` e `lock ("myLock")` violam essa diretriz:

- `lock (this)` é um problema se a instância pode ser acessada publicamente.

- `lock (typeof (MyType))` é um problema se `MyType` está acessível publicamente.

- `lock("myLock")` é um problema porque qualquer outro código no processo usando a mesma cadeia de caracteres compartilhará o mesmo bloqueio.

A prática recomendada é definir um objeto `private` para bloquear ou uma variável de objeto `private static` para proteger dados comuns a todas as instâncias.

Não é possível usar a palavra-chave [await](await.md) no corpo de uma instrução `lock`.

## <a name="example---threads-without-locking"></a>Exemplo – threads sem bloqueio

O exemplo a seguir mostra um uso simples de threads sem bloqueio em C#:

[!code-csharp[csrefKeywordsFixedLock#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#5)]

## <a name="example---threads-using-locking"></a>Exemplo – Threads usando bloqueio

O exemplo a seguir usa threads e `lock`. Enquanto a instrução `lock` estiver presente, o bloco de instrução será uma seção crítica e `balance` nunca se tornará um número negativo:

[!code-csharp[csrefKeywordsFixedLock#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#6)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- <xref:System.Reflection.MethodImplAttributes>
- <xref:System.Threading.Mutex>
- <xref:System.Threading.Monitor>
- [Referência de C#](../../language-reference/index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Threading](../../programming-guide/concepts/threading/index.md)
- [Palavras-chave do C#](index.md)
- [Palavras-chave de instrução](statement-keywords.md)
- [Operações interconectadas](../../../standard/threading/interlocked-operations.md)
- [AutoResetEvent](../../../standard/threading/autoresetevent.md)
- [Sincronização de Thread ](../../programming-guide/concepts/threading/thread-synchronization.md)