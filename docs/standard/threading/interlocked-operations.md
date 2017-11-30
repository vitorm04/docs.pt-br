---
title: "Operações interconectadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 122058b7e826e27fe6c60c5b07610f7c63e64f78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="interlocked-operations"></a>Operações interconectadas
O <xref:System.Threading.Interlocked> classe fornece métodos que sincronizam o acesso a uma variável que é compartilhada por vários threads. Os threads de processos diferentes podem usar esse mecanismo se a variável estiver na memória compartilhada. Operações interconectadas são atômicas — ou seja, toda a operação é uma unidade que não pode ser interrompida por outra operação sincronizada na mesma variável. Isso é importante em sistemas de operacionais com preemptivo multithreading, onde um thread pode ser suspenso após o carregamento de um valor de um endereço de memória, mas antes de ter a chance de alterá-lo e armazená-lo.  
  
 O <xref:System.Threading.Interlocked> classe fornece as seguintes operações:  
  
-   No .NET Framework versão 2.0, o <xref:System.Threading.Interlocked.Add%2A> método adiciona um valor inteiro para uma variável e retorna o novo valor da variável.  
  
-   No .NET Framework versão 2.0, o <xref:System.Threading.Interlocked.Read%2A> método lê um valor inteiro de 64 bits, como uma operação atômica. Isso é útil em sistemas operacionais de 32 bits, onde a leitura de um inteiro de 64 bits não é normalmente uma operação atômica.  
  
-   O <xref:System.Threading.Interlocked.Increment%2A> e <xref:System.Threading.Interlocked.Decrement%2A> métodos incrementar ou decrementar uma variável e retornar o valor resultante.  
  
-   O <xref:System.Threading.Interlocked.Exchange%2A> método executa uma troca atômica do valor em uma variável especificada, retornando o valor e substituí-lo com um novo valor. No .NET Framework versão 2.0, uma sobrecarga desse método genérica pode ser usada para realizar essa troca em uma variável de qualquer tipo de referência. Consulte <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   O <xref:System.Threading.Interlocked.CompareExchange%2A> método também troca dois valores, mas contingente no resultado de uma comparação. No .NET Framework versão 2.0, uma sobrecarga desse método genérica pode ser usada para realizar essa troca em uma variável de qualquer tipo de referência. Consulte <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 Processadores modernos, os métodos do <xref:System.Threading.Interlocked> classe geralmente pode ser implementada por uma única instrução. Portanto, eles fornecem sincronização de alto desempenho e pode ser usados para criar mecanismos de sincronização de nível superior, como bloqueios de rotação.  
  
 Para obter um exemplo que usa o <xref:System.Threading.Monitor> e <xref:System.Threading.Interlocked> classes de combinação, consulte [monitores](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>Exemplo de CompareExchange  
 O <xref:System.Threading.Interlocked.CompareExchange%2A> método pode ser usado para proteger os cálculos que são mais complicados do que simples incremento e decremento. O exemplo a seguir demonstra um método de thread-safe que adiciona a um total de execução armazenado como um flutuante número de ponto. (Para inteiros, o <xref:System.Threading.Interlocked.Add%2A> método é uma solução mais simples.) Para obter exemplos de código completo, consulte as sobrecargas de <xref:System.Threading.Interlocked.CompareExchange%2A> que recebem argumentos de ponto flutuantes de precisão simples e precisão dupla (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> e <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Sem tipo sobrecargas do Exchange e CompareExchange  
 O <xref:System.Threading.Interlocked.Exchange%2A> e <xref:System.Threading.Interlocked.CompareExchange%2A> métodos têm sobrecargas que usam argumentos de tipo <xref:System.Object>. É o primeiro argumento de cada essas sobrecargas `ref Object` (`ByRef … As Object` no Visual Basic), e segurança de tipo requer que a variável passada para este argumento para ser digitado estritamente como <xref:System.Object>; você simplesmente não é possível converter o primeiro argumento para o tipo <xref:System.Object> ao chamar esses métodos.  
  
> [!NOTE]
>  No .NET Framework versão 2.0, use as sobrecargas genéricas do <xref:System.Threading.Interlocked.Exchange%2A> e <xref:System.Threading.Interlocked.CompareExchange%2A> métodos para trocar fortemente tipados variáveis.  
  
 O exemplo de código a seguir mostra uma propriedade do tipo `ClassA` que pode ser definida apenas uma vez, como ele pode ser implementado no .NET Framework versão 1.0 ou 1.1.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [Threading](../../../docs/standard/threading/index.md)  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
