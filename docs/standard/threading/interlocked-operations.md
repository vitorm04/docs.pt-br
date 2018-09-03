---
title: Operações interconectadas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 361e618578e836e10cf8655f027bed42eac7affd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393133"
---
# <a name="interlocked-operations"></a>Operações interconectadas
A classe <xref:System.Threading.Interlocked> fornece métodos que sincronizam o acesso a uma variável que é compartilhada por vários threads. Os threads de processos diferentes podem usar esse mecanismo se a variável estiver na memória compartilhada. Operações interconectadas são atômicas — ou seja, toda a operação é uma unidade que não pode ser interrompida por outra operação interconectada na mesma variável. Isso é importante em sistemas de operacionais com multithreading preemptivo, onde um thread pode ser suspenso após o carregamento de um valor de um endereço de memória, mas antes de ter a chance de alterá-lo e armazená-lo.  
  
 A classe <xref:System.Threading.Interlocked> fornece as seguintes operações:  
  
-   No .NET Framework versão 2.0, o método <xref:System.Threading.Interlocked.Add%2A> adiciona um valor inteiro a uma variável e retorna o novo valor da variável.  
  
-   No .NET Framework versão 2.0, o método <xref:System.Threading.Interlocked.Read%2A> lê um valor inteiro de 64 bits como uma operação atômica. Isso é útil em sistemas operacionais de 32 bits, onde a leitura de um inteiro de 64 bits não é normalmente uma operação atômica.  
  
-   Os métodos <xref:System.Threading.Interlocked.Increment%2A> e <xref:System.Threading.Interlocked.Decrement%2A> incrementam ou reduzem uma variável e retornam o valor resultante.  
  
-   O método <xref:System.Threading.Interlocked.Exchange%2A> executa uma troca atômica do valor em uma variável especificada, retornando esse valor e o substituindo por um valor novo. No .NET Framework versão 2.0, uma sobrecarga genérica desse método pode ser usada para realizar essa troca em uma variável de qualquer tipo de referência. Consulte <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   O método <xref:System.Threading.Interlocked.CompareExchange%2A> também troca dois valores, mas depende do resultado de uma comparação. No .NET Framework versão 2.0, uma sobrecarga genérica desse método pode ser usada para realizar essa troca em uma variável de qualquer tipo de referência. Consulte <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 Em processadores modernos, os métodos da classe <xref:System.Threading.Interlocked> geralmente podem ser implementados por uma única instrução. Portanto, eles fornecem sincronização de alto desempenho e podem ser usados para criar mecanismos de sincronização de nível superior, como bloqueios de rotação.  
  
 Para obter um exemplo que usa as classes <xref:System.Threading.Monitor> e <xref:System.Threading.Interlocked> em combinação, consulte [Monitores](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>Exemplo de CompareExchange  
 O método <xref:System.Threading.Interlocked.CompareExchange%2A> pode ser usado para proteger os cálculos que são mais complicados do que simples incrementos e reduções. O exemplo a seguir demonstra um método de thread-safe que adiciona a um total de execução armazenado como um número de ponto flutuante. (Para inteiros, o método <xref:System.Threading.Interlocked.Add%2A> é uma solução mais simples). Para obter exemplos de código completo, consulte as sobrecargas de <xref:System.Threading.Interlocked.CompareExchange%2A> que recebem argumentos de ponto flutuante de precisão simples e precisão dupla (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> e <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Sobrecargas sem tipo do Exchange e CompareExchange  
 Os métodos <xref:System.Threading.Interlocked.Exchange%2A> e <xref:System.Threading.Interlocked.CompareExchange%2A> têm sobrecargas que usam argumentos do tipo <xref:System.Object>. O primeiro argumento de cada uma essas sobrecargas é `ref Object` (`ByRef … As Object` no Visual Basic), e a segurança de tipos exige que a variável passada para este argumento seja digitada estritamente como <xref:System.Object>; você não pode apenas converter o primeiro argumento para o tipo <xref:System.Object> ao chamar esses métodos.  
  
> [!NOTE]
>  No .NET Framework versão 2.0, use as sobrecargas genéricas dos métodos <xref:System.Threading.Interlocked.Exchange%2A> e <xref:System.Threading.Interlocked.CompareExchange%2A> para trocar variáveis fortemente tipadas.  
  
 O exemplo de código a seguir mostra uma propriedade do tipo `ClassA` que pode ser definida apenas uma vez, pois pode ser implementada no .NET Framework versão 1.0 ou 1.1.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [Threading](../../../docs/standard/threading/index.md)  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
