---
title: Como declarar e usar um delegado e criar uma instância dele (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 6c53d7572074db44976494e5eed596bf95aaf456
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858854"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Como declarar e usar um delegado e criar uma instância dele (Guia de Programação em C#)
No C# 1.0 e versões posteriores, é possível declarar delegados conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 O C# 2.0 oferece uma maneira mais simples de gravar a declaração anterior, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 No C# 2.0 e versões posteriores, também é possível usar um método anônimo para declarar e inicializar um [delegado](../../../csharp/language-reference/keywords/delegate.md), conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 No C# 3.0 e versões posteriores, os delegados também podem ser declarados e instanciados usando uma expressão lambda, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 Para obter mais informações, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 O exemplo a seguir ilustra a declaração, instanciação e o uso de um delegado. A classe `BookDB` encapsula um banco de dados de uma livraria que mantém um banco de dados de livros. Ela expõe um método, `ProcessPaperbackBooks`, que localiza todos os livros de bolso no banco de dados e chama um delegado para cada um. O tipo `delegate` usado tem o nome `ProcessBookDelegate`. A classe `Test` usa essa classe para imprimir os títulos e o preço médio dos livros de bolso.  
  
 O uso de delegados promove uma boa separação de funcionalidade entre o banco de dados da livraria e o código de cliente. O código de cliente não tem conhecimento de como os livros são armazenados ou como o código da livraria localiza os livros de bolso. O código da livraria não tem conhecimento do processamento executado nos livros de bolso após a localização.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a>Programação robusta  
  
-   Declarando um delegado.  
  
     A instrução a seguir declara um novo tipo de delegado.  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     Cada tipo de delegado descreve o número e os tipos dos argumentos e o tipo do valor retornado dos métodos que pode encapsular. Sempre que um novo conjunto de tipos de argumento ou tipo de valor retornado for necessário, um novo tipo de delegado deverá ser declarado.  
  
-   Instanciando um delegado.  
  
     Após a declaração do tipo de delegado, um objeto delegado deve ser criado e associado a um método específico. No exemplo anterior, faça isso passando o método `PrintTitle` para o método `ProcessPaperbackBooks`, como no exemplo a seguir:  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     Isso cria um novo objeto delegado associado ao método [estático](../../../csharp/language-reference/keywords/static.md) `Test.PrintTitle`. Da mesma forma, o método não estático `AddBookToTotal` no objeto `totaller` é passado como no exemplo a seguir:  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     Em ambos os casos, um novo objeto delegado é passado para o método `ProcessPaperbackBooks`.  
  
     Após a criação de um delegado, o método ao qual ele está associado nunca se altera; objetos delegados são imutáveis.  
  
-   Chamando um delegado.  
  
     Normalmente, o objeto delegado, após sua criação, é passado para outro código que chamará o delegado. Um objeto delegado é chamado usando seu nome seguido dos argumentos entre parênteses a serem passados para o delegado. A seguir, veja um exemplo de uma chamada de delegado:  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     Um delegado pode ser chamado de forma síncrona, como neste exemplo ou de forma assíncrona, usando os métodos `BeginInvoke` e `EndInvoke`.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Eventos](../../../csharp/programming-guide/events/index.md)  
- [Delegados](../../../csharp/programming-guide/delegates/index.md)
