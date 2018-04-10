---
title: Instrução using (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a>Instrução using (Referência de C#)
Fornece uma sintaxe conveniente que garante o uso correto de objetos <xref:System.IDisposable>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a instrução using.  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>Comentários  
 <xref:System.IO.File> e <xref:System.Drawing.Font> são exemplos de tipos gerenciados que acessam recursos não gerenciados (nesse caso, identificadores de arquivo de caso e contextos de dispositivo). Há muitos outros tipos de recursos não gerenciados e tipos de biblioteca de classes que os encapsula. Todos esses tipos devem implementar a interface <xref:System.IDisposable>.  
  
Quando o tempo de vida de um `IDisposable` objeto está limitado a um único método, você deve declarar e instanciá-la em um `using` instrução. A instrução `using` chama o método <xref:System.IDisposable.Dispose%2A> no objeto da forma correta e (quando você o usa como mostrado anteriormente) ele também faz com que o objeto em si saia do escopo assim que <xref:System.IDisposable.Dispose%2A> é chamado. Dentro do bloco `using`, o objeto é somente leitura e não pode ser modificado ou reatribuído.  
  
 A instrução `using` garante que <xref:System.IDisposable.Dispose%2A> seja chamado mesmo se ocorrer uma exceção enquanto você estiver chamando métodos no objeto. Você pode obter o mesmo resultado colocando o objeto dentro de um bloco try e, em seguida, chamando <xref:System.IDisposable.Dispose%2A> em um bloco finally. Na verdade, é dessa forma que a instrução `using` é convertida pelo compilador. O exemplo de código anterior se expande para o seguinte código em tempo de compilação (observe as chaves extras para criar o escopo limitado para o objeto):  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 Várias instâncias de um tipo podem ser declaradas em uma instrução `using`, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 Você pode criar uma instância do objeto de recurso e, em seguida, passar a variável para a instrução `using`, mas isso não é uma prática recomendada. Nesse caso, o objeto permanece no escopo depois que o controle sai do bloco `using` mesmo que provavelmente ele não tenha mais acesso aos seus recursos não gerenciados. Em outras palavras, ele será não será mais totalmente inicializado. Se você tentar usar o objeto fora do bloco `using`, corre o risco de causar o lançamento de uma exceção. Por esse motivo, geralmente é melhor instanciar o objeto na instrução `using` e limitar seu escopo ao bloco `using`.  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
Para obter mais informações sobre como descartar `IDisposable` objetos, consulte [usando objetos que implementam IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Diretiva using](../../../csharp/language-reference/keywords/using-directive.md)  
 [Coleta de lixo](../../../standard/garbage-collection/index.md)  
 [Usando objetos que implementam IDisposable](../../../standard/garbage-collection/using-objects.md)  
 [Interface IDisposable](xref:System.IDisposable)
