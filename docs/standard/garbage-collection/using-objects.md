---
title: Usando objetos que implementam IDisposable
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c586c725a385029db80763ba13915be79c6cd7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-objects-that-implement-idisposable"></a>Usando objetos que implementam IDisposable

O coletor de lixo do Common Language Runtime recupera a memória usada por objetos gerenciados, mas os tipos que usam recursos não gerenciados implementam a interface <xref:System.IDisposable> para permitir que a memória alocada para esses recursos não gerenciados seja recuperada. Após terminar de usar um objeto que implementa <xref:System.IDisposable>, você deverá chamar a implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> do objeto. Você pode fazer isso de duas maneiras:  
  
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
  
A instrução `using` do C# também permite que você adquira vários recursos em uma única instrução, o que é internamente equivalente a instruções `using` aninhadas. O exemplo a seguir cria instancia dois objetos <xref:System.IO.StreamReader> para ler o conteúdo de dois arquivos diferentes.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Bloco Try/finally

Em vez de incluir um bloco `try/finally` em uma instrução `using`, você pode optar por implementar diretamente o bloco `try/finally`. Esse pode ser o estilo pessoal de codificação ou talvez você queira fazer isso por um dos seguintes motivos:  
  
* Para incluir um bloco `catch` para lidar com algumas exceções geradas no bloco `try`. Caso contrário, todas as exceções geradas pela instrução `using` não são manipuladas, assim como em quaisquer exceções geradas dentro do bloco `using` se um bloco `try/catch` não estiver presente.  
  
* Para criar uma instância de um objeto que implementa <xref:System.IDisposable> cujo escopo não é local para o bloco dentro do qual é declarado.  
  
O exemplo a seguir é semelhante ao exemplo anterior, exceto que ele usa um bloco `try/catch/finally` para criar uma instância, usar e descartar um objeto <xref:System.IO.StreamReader> e também para manipular todas as exceções lançadas pelo construtor <xref:System.IO.StreamReader> e pelo método <xref:System.IO.StreamReader.ReadToEnd%2A>. Observe que o código no bloco `finally` verifica se o objeto que implementa <xref:System.IDisposable> não é `null` antes de chamar o método <xref:System.IDisposable.Dispose%2A>. Não fazer isso poderá levar a uma exceção de <xref:System.NullReferenceException> em tempo de execução.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Você poderá seguir esse padrão básico se optar por implementar ou precisar implementar um bloco `try/finally`, pois a linguagem de programação não oferece suporte a uma instrução `using`, mas permite chamadas diretas para o método <xref:System.IDisposable.Dispose%2A>. 
  
## <a name="see-also"></a>Consulte também

[Limpando recursos não gerenciados](../../../docs/standard/garbage-collection/unmanaged.md)   
[Instrução using (Referência de C#)](~/docs/csharp/language-reference/keywords/using-statement.md)   
[Instrução Using (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
