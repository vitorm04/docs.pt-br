---
title: "Como declarar e usar um delegado e criar uma inst&#226;ncia dele (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "delegados [C#], declarando e instanciando"
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como declarar e usar um delegado e criar uma inst&#226;ncia dele (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

No C\# 1.0 e posterior, os delegados podem ser declarados como mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-cs[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C\# 2.0 fornece uma maneira mais simples de escrever a declaração anterior, conforme mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 No C\# 2.0 e posteriores, também é possível usar um método anônimo para declarar e inicializar um  [delegar](../../../csharp/language-reference/keywords/delegate.md), conforme mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 No C\# 3.0 e posterior, delegados podem também ser declarados e instanciados usando uma expressão lambda, conforme mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 Para obter mais informações, consulte [Expressões lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 O exemplo a seguir ilustra a declarar, instanciar e usar um delegado.  O `BookDB` classe encapsula um banco de dados da livraria que mantém um banco de dados de livros.  Ele expõe um método, `ProcessPaperbackBooks`, que localiza o papel de jornal todos os livros no banco de dados e chama um delegado para cada um deles.  O `delegate` tipo usado é denominado `ProcessBookDelegate`.  O `Test` classe usa essa classe para imprimir os títulos e o preço médio dos livros jornal.  
  
 A utilização de delegados promove uma boa separação de funcionalidade entre o banco de dados da livraria e o código do cliente.  O código do cliente não tem conhecimento de como os livros são armazenados ou como o código da livraria encontra livros de jornal.  O código da livraria não tem conhecimento do qual processamento é realizado no jornal livros após ele encontrá\-las.  
  
## Exemplo  
 [!code-cs[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## Programação robusta  
  
-   Declarar um delegado.  
  
     A instrução a seguir declara um novo tipo de delegado.  
  
     [!code-cs[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     Cada tipo delegado descreve o número e tipos dos argumentos e o tipo de valor de retorno de métodos que ele pode encapsular.  Sempre que for necessário um novo conjunto de tipos de argumento ou tipo de valor de retorno, um novo tipo de delegado deve ser declarado.  
  
-   Criar uma instância de um delegado.  
  
     Após ter sido declarado um tipo delegate, um objeto delegado deve ser criado e associado a um método específico.  No exemplo anterior, faça isso passando a `PrintTitle` método para o `ProcessPaperbackBooks` método como no exemplo a seguir:  
  
     [!code-cs[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     Isso cria um novo objeto delegado, associado com o  [estático](../../../csharp/language-reference/keywords/static.md) método `Test.PrintTitle`.  Da mesma forma, o método non\-static `AddBookToTotal` no objeto `totaller` é passado como no exemplo a seguir:  
  
     [!code-cs[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     Em ambos os casos, um novo objeto delegado é passado para o `ProcessPaperbackBooks` método.  
  
     Depois de um delegado é criado, o método está associado nunca alterações; delegado são imutáveis.  
  
-   Chamar um delegado.  
  
     Após a criação de um objeto delegado, o objeto delegado normalmente é passado para outro código que entrará em contato com o delegado.  Um objeto delegado é chamado usando o nome do objeto delegado, seguido pelos argumentos entre parênteses a serem passados ao delegado.  Veja a seguir um exemplo de uma chamada de representante:  
  
     [!code-cs[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     Um delegado pode ser tanto chamado de forma síncrona, como no exemplo, ou assincronamente usando `BeginInvoke` e `EndInvoke` métodos.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Eventos](../../../csharp/programming-guide/events/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)