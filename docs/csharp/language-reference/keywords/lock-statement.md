---
title: "Instrução lock (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
dev_langs:
- CSharp
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 020be199391789360ae9a25858bef54d8259ae56
ms.lasthandoff: 03/13/2017

---
# <a name="lock-statement-c-reference"></a>Instrução lock (Referência de C#)
A palavra-chave `lock` marca um bloco de instruções como uma seção crítica obtendo o bloqueio de exclusão mútua para um determinado objeto, executando uma instrução e, em seguida, liberando o bloqueio. O exemplo a seguir inclui uma instrução `lock`.  
  
```  
  
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
  
 Para obter mais informações, consulte [Sincronização de thread](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4).  
  
## <a name="remarks"></a>Comentários  
 A palavra-chave `lock` garante que um thread não insere uma seção crítica do código enquanto outro thread está na seção crítica. Se outro thread tentar inserir um código bloqueado, ele aguardará, bloqueado, até que o objeto seja liberado.  
  
 A seção [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) discute o threading.  
  
 A palavra-chave `lock` chama <xref:System.Threading.Monitor.Enter%2A> no início do bloco e <xref:System.Threading.Monitor.Exit%2A> no final do bloco. Uma <xref:System.Threading.ThreadInterruptedException> será gerada se <xref:System.Threading.Thread.Interrupt%2A> interromper um thread que está esperando para inserir uma instrução `lock`.  
  
 Em geral, evite o bloqueio em um tipo `public` ou instâncias além do controle do código. Os constructos comuns `lock (this)`, `lock (typeof (MyType))` e `lock ("myLock")` violam essa diretriz:  
  
-   `lock (this)` é um problema se a instância pode ser acessada publicamente.  
  
-   `lock (typeof (MyType))` é um problema se `MyType` está acessível publicamente.  
  
-   `lock("myLock")` é um problema porque qualquer outro código no processo usando a mesma cadeia de caracteres compartilhará o mesmo bloqueio.  
  
 A prática recomendada é definir um objeto `private` para bloquear ou uma variável de objeto `private static` para proteger dados comuns a todas as instâncias.  
  
 Não é possível usar a palavra-chave [await](../../../csharp/language-reference/keywords/await.md) no corpo de uma instrução `lock`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um uso simples de threads sem bloqueio em C#.  
  
 [!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa threads e `lock`. Enquanto a instrução `lock` estiver presente, o bloco de instrução será uma seção crítica e `balance` nunca se tornará um número negativo.  
  
 [!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.MethodImplAttributes>   
 <xref:System.Threading.Mutex>   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras-chave de instrução](../../../csharp/language-reference/keywords/statement-keywords.md)   
 @System.Threading.Monitor   
 [Operações interconectadas](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b)   
 [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18)   
 [Sincronização de Thread ](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)
