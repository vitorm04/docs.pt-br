---
title: "Instru&#231;&#227;o lock (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "lock_CSharpKeyword"
  - "lock"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave lock [C#]"
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
caps.handback.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Instru&#231;&#227;o lock (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A palavra\-chave de marca `lock` um bloco de declaração como uma seção crítica obtendo o bloqueio de mútuo\- exclusão para um determinado objeto, executando uma instrução e em seguida, liberando o bloqueio.  O exemplo a seguir inclui uma declaração de `lock` .  
  
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
  
 Para mais informações, consulte [Sincronização de thread](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Comentários  
 A palavra\-chave de `lock` garante que um segmento não insira uma seção de código crítico quando outro segmento está na seção crítica.  Se outro segmento tenta digitar um código bloqueado, esperará, para bloquear, até que o objeto seja liberado.  
  
 A seção discute [Threading](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md) segmentação.  
  
 A palavra\-chave de `lock` chama <xref:System.Threading.Monitor.Enter%2A> no início do bloco e <xref:System.Threading.Monitor.Exit%2A> no final do bloco.  <xref:System.Threading.ThreadInterruptedException> é lançada se <xref:System.Threading.Thread.Interrupt%2A> interrompe segmento que está aguardando para inserir uma instrução de `lock` .  
  
 Em geral, evite bloqueio em um tipo de `public` , ou instâncias além de controle do seu código.  Um comum constrói `lock (this)`, `lock (typeof (MyType))`, e `lock ("myLock")` viola essa diretriz:  
  
-   `lock (this)` é um problema se a instância pode ser acessada publicamente.  
  
-   `lock (typeof (MyType))` é um problema se `MyType` é publicamente acessível.  
  
-   `lock("myLock")` é um problema pois qualquer outro código no processo usando a mesma cadeia de caracteres, compartilhar o mesmo bloqueio.  
  
 A prática recomendada é definir em um objeto de `private` ao bloqueio, ou uma variável de objeto de `private static` para proteger dados comuns a todas as instâncias.  
  
 Você não pode usar a palavra\-chave de [espere](../../../csharp/language-reference/keywords/await.md) no corpo de uma instrução de `lock` .  
  
## Exemplo  
 O exemplo a seguir mostra um uso simples de segmentos sem bloqueio em C\#.  
  
 [!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## Exemplo  
 O exemplo a seguir usa segmentos e `lock`.  Como a instrução de `lock` estiverem presentes, o bloco de declaração é uma seção crítica e `balance` nunca se tornará um número negativo.  
  
 [!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Reflection.MethodImplAttributes>   
 <xref:System.Threading.Mutex>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Threading](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras\-chave de instrução](../../../csharp/language-reference/keywords/statement-keywords.md)   
 [Monitores](../Topic/Monitors.md)   
 [Operações interconectadas](../Topic/Interlocked%20Operations.md)   
 [AutoResetEvent](../Topic/AutoResetEvent.md)   
 [Sincronização de thread](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)