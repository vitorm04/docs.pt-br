---
title: Instrução lock (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2ce870e8caa67d780ce603a6f1dbcc7cd303b842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274213"
---
# <a name="lock-statement-c-reference"></a>Instrução lock (Referência de C#)
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
  
-   `lock (this)` é um problema se a instância pode ser acessada publicamente.  
  
-   `lock (typeof (MyType))` é um problema se `MyType` está acessível publicamente.  
  
-   `lock("myLock")` é um problema porque qualquer outro código no processo usando a mesma cadeia de caracteres compartilhará o mesmo bloqueio.  
  
 A prática recomendada é definir um objeto `private` para bloquear ou uma variável de objeto `private static` para proteger dados comuns a todas as instâncias.  
  
 Não é possível usar a palavra-chave [await](../../../csharp/language-reference/keywords/await.md) no corpo de uma instrução `lock`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um uso simples de threads sem bloqueio em C#.  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa threads e `lock`. Enquanto a instrução `lock` estiver presente, o bloco de instrução será uma seção crítica e `balance` nunca se tornará um número negativo.  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Threading](../../programming-guide/concepts/threading/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Palavras-chave de instrução](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [Operações interconectadas](../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../standard/threading/autoresetevent.md)  
 [Sincronização de Thread ](../../programming-guide/concepts/threading/thread-synchronization.md)
