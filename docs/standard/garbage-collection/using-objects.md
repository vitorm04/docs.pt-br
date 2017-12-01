---
title: Usando objetos que implementam IDisposable
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd78c2f99ca5c8ffe3c753e158ceba3e0c458c5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-objects-that-implement-idisposable"></a>Usando objetos que implementam IDisposable

O coletor de lixo do common language runtime recupera a memória usada por objetos gerenciados, mas os tipos que usam recursos não gerenciados implementar o <xref:System.IDisposable> interface para permitir que a memória alocada para esses recursos não gerenciados a ser recuperada. Após terminar de usar um objeto que implementa <xref:System.IDisposable>, você deverá chamar a implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> do objeto. Você pode fazer isso de duas maneiras:  
  
* Com a instrução `using` do C# ou a instrução `Using` do Visual Basic.  
  
* Implementando um bloco `try/finally`.  

## <a name="the-using-statement"></a>A instrução using

A instrução `using` no C# e a instrução `Using` no Visual Basic simplificam o código que você deve escrever para criar e limpar um objeto. A instrução `using` obtém um ou mais recursos, executa as instruções que você especifica e descarta o objeto automaticamente. Entretanto, a instrução `using` é útil apenas para os objetos que são usados no escopo do método no qual eles são criados.  
  
O exemplo a seguir usa a instrução `using` para criar e liberar um objeto <xref:System.IO.StreamReader?displayProperty=nameWithType>.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Observe que, embora a classe <xref:System.IO.StreamReader> implemente a interface <xref:System.IDisposable>, o que indica que ela usa um recurso não gerenciado, o exemplo não chama explicitamente o método <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType>. Quando o compilador do C# ou do Visual Basic encontra a instrução `using`, ele emite a IL (linguagem intermediária) que equivale ao seguinte código que contém explicitamente um bloco `try/finally`.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` instrução também permite que você adquira vários recursos em uma única instrução, que equivale internamente aninhadas `using` instruções. O exemplo a seguir cria instancia dois objetos <xref:System.IO.StreamReader> para ler o conteúdo de dois arquivos diferentes.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Bloco Try/finally

Em vez de incluir um bloco `try/finally` em uma instrução `using`, você pode optar por implementar diretamente o bloco `try/finally`. Esse pode ser o estilo pessoal de codificação ou talvez você queira fazer isso por um dos seguintes motivos:  
  
* Para incluir um bloco `catch` para lidar com algumas exceções geradas no bloco `try`. Caso contrário, todas as exceções geradas pela instrução `using` não são manipuladas, assim como em quaisquer exceções geradas dentro do bloco `using` se um bloco `try/catch` não estiver presente.  
  
* Para criar uma instância de um objeto que implementa <xref:System.IDisposable> cujo escopo não é local para o bloco dentro do qual é declarado.  
  
O exemplo a seguir é semelhante ao exemplo anterior, exceto que ele usa um `try/catch/finally` blocos para criar uma instância, use e descartar um <xref:System.IO.StreamReader> objeto e para lidar com as exceções geradas pelo <xref:System.IO.StreamReader> construtor e seu <xref:System.IO.StreamReader.ReadToEnd%2A> método. Observe que o código no bloco `finally` verifica se o objeto que implementa <xref:System.IDisposable> não é `null` antes de chamar o método <xref:System.IDisposable.Dispose%2A>. Não fazer isso poderá levar a uma exceção de <xref:System.NullReferenceException> em tempo de execução.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Você pode seguir este padrão básico se você optar por implementar ou deve implementar um `try/finally` bloquear, como a linguagem de programação não dá suporte uma `using` instrução, mas permite chamadas diretas para o <xref:System.IDisposable.Dispose%2A> método. 
  
## <a name="see-also"></a>Consulte também

[Limpando recursos não gerenciados](../../../docs/standard/garbage-collection/unmanaged.md)   
[usando a instrução (referência de c#)](~/docs/csharp/language-reference/keywords/using-statement.md)   
[Usando a instrução (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
