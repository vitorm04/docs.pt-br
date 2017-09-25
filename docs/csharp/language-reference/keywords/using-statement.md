---
title: "Instrução using (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 201dde951b4f92d92b7d78b3d71a3f3cfb559507
ms.contentlocale: pt-br
ms.lasthandoff: 09/25/2017

---
# <a name="using-statement-c-reference"></a>Instrução using (Referência de C#)
Fornece uma sintaxe conveniente que garante o uso correto de objetos <xref:System.IDisposable>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a instrução using.  
  
 [!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>Comentários  
 <xref:System.IO.File> e <xref:System.Drawing.Font> são exemplos de tipos gerenciados que acessam recursos não gerenciados (nesse caso, identificadores de arquivo de caso e contextos de dispositivo). Há muitos outros tipos de recursos não gerenciados e tipos de biblioteca de classes que os encapsula. Todos esses tipos devem implementar a interface <xref:System.IDisposable>.  
  
 Como regra, quando você usa um objeto `IDisposable`, você deve declará-la e criar uma instância dela em uma instrução `using`. A instrução `using` chama o método <xref:System.IDisposable.Dispose%2A> no objeto da forma correta e (quando você o usa como mostrado anteriormente) ele também faz com que o objeto em si saia do escopo assim que <xref:System.IDisposable.Dispose%2A> é chamado. Dentro do bloco `using`, o objeto é somente leitura e não pode ser modificado ou reatribuído.  
  
 A instrução `using` garante que <xref:System.IDisposable.Dispose%2A> seja chamado mesmo se ocorrer uma exceção enquanto você estiver chamando métodos no objeto. Você pode obter o mesmo resultado colocando o objeto dentro de um bloco try e, em seguida, chamando <xref:System.IDisposable.Dispose%2A> em um bloco finally. Na verdade, é dessa forma que a instrução `using` é convertida pelo compilador. O exemplo de código anterior se expande para o seguinte código em tempo de compilação (observe as chaves extras para criar o escopo limitado para o objeto):  
  
 [!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 Várias instâncias de um tipo podem ser declaradas em uma instrução `using`, conforme mostrado no exemplo a seguir.  
  
 [!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 Você pode criar uma instância do objeto de recurso e, em seguida, passar a variável para a instrução `using`, mas isso não é uma prática recomendada. Nesse caso, o objeto permanece no escopo depois que o controle sai do bloco `using` mesmo que provavelmente ele não tenha mais acesso aos seus recursos não gerenciados. Em outras palavras, ele será não será mais totalmente inicializado. Se você tentar usar o objeto fora do bloco `using`, corre o risco de causar o lançamento de uma exceção. Por esse motivo, geralmente é melhor instanciar o objeto na instrução `using` e limitar seu escopo ao bloco `using`.  
  
 [!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Diretiva using](../../../csharp/language-reference/keywords/using-directive.md)   
 [Coleta de lixo](../../../standard/garbage-collection/index.md)   
 [Implementando um método dispose](../../../standard/garbage-collection/implementing-dispose.md)

