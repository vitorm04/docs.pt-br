---
title: "Instruções (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 166130ca7a63127d0bd1df8328dc08b4a8cd7845
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="statements-c-programming-guide"></a>Instruções (Guia de Programação em C#)
As ações que usa um programa executa são expressas em instruções. Ações comuns incluem declarar variáveis, atribuir valores, chamar métodos, fazer loops pelas coleções e ramificar para um ou para outro bloco de código, dependendo de uma determinada condição. A ordem na qual as instruções são executadas em um programa é chamada de fluxo de controle ou fluxo de execução. O fluxo de controle pode variar sempre que um programa é executado, dependendo de como o programa reage às entradas que recebe em tempo de execução.  
  
 Uma instrução pode consistir em uma única linha de código que termina em um ponto e vírgula ou uma série de instruções de uma linha em um bloco. Um bloco de instrução é colocado entre colchetes {} e pode conter blocos aninhados. O código a seguir mostra dois exemplos de instruções de linha única, bem como um bloco de instrução de várias linhas:  
  
 [!code-csharp[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## <a name="types-of-statements"></a>Tipos de instruções  
 A tabela a seguir lista os diferentes tipos de instruções em C# e as palavras-chave associadas a elas, com links para tópicos que contêm mais informações:  
  
|Categoria|Palavras-chave do C#/observações|  
|--------------|---------------------------|  
|Instruções de declaração|Uma declaração de instrução introduz uma nova variável ou constante. Uma declaração variável pode, opcionalmente, atribuir um valor à variável. Uma declaração constante, a atribuição é obrigatória.<br /><br /> [!code-csharp[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]|  
|Instruções de expressão|Instruções de expressão que calculam um valor devem armazenar o valor em uma variável.<br /><br /> [!code-csharp[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]|  
|[Instruções de seleção](../../../csharp/language-reference/keywords/selection-statements.md)|Instruções de seleção permitem que você ramifique para diferentes seções de código, dependendo de uma ou mais condições especificadas. Para mais informações, consulte os seguintes tópicos:<br /><br /> [if](../../../csharp/language-reference/keywords/if-else.md), [else](../../../csharp/language-reference/keywords/if-else.md), [switch](../../../csharp/language-reference/keywords/switch.md), [case](../../../csharp/language-reference/keywords/switch.md)|  
|[Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)|Instruções de iteração permitem que você percorra coleções como matrizes ou execute o mesmo conjunto de instruções repetidamente até que uma determinada condição seja atendida. Para mais informações, consulte os seguintes tópicos:<br /><br /> [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), [foreach](../../../csharp/language-reference/keywords/foreach-in.md), [in](../../../csharp/language-reference/keywords/foreach-in.md), [while](../../../csharp/language-reference/keywords/while.md)|  
|[Instruções de hiperlink](../../../csharp/language-reference/keywords/jump-statements.md)|Instruções de hiperlink transferem o controle para outra seção de código. Para mais informações, consulte os seguintes tópicos:<br /><br /> [break](../../../csharp/language-reference/keywords/break.md), [continue](../../../csharp/language-reference/keywords/continue.md), [default](../../../csharp/language-reference/keywords/switch.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), [yield](../../../csharp/language-reference/keywords/yield.md)|  
|[Instruções para tratamento de exceções](../../../csharp/language-reference/keywords/exception-handling-statements.md)|Instruções para tratamento de exceções permitem que você se recupere normalmente de condições excepcionais que ocorrem em tempo de execução. Para mais informações, consulte os seguintes tópicos:<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md), [try-catch](../../../csharp/language-reference/keywords/try-catch.md), [try-finally](../../../csharp/language-reference/keywords/try-finally.md), [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Checked e unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|As instruções checked e unchecked permitem que você especifique se operações numéricas podem causar um estouro quando o resultado for armazenado em uma variável que é muito pequena para conter o valor resultante. Para obter mais informações, consulte [checked](../../../csharp/language-reference/keywords/checked.md) e [unchecked](../../../csharp/language-reference/keywords/unchecked.md).|  
|A instrução `await`|Se marcar um método com o modificador [async](../../../csharp/language-reference/keywords/async.md), você poderá usar o operador [await](../../../csharp/language-reference/keywords/await.md) no método. Quando o controle atinge uma expressão `await` no método assíncrono, ele retorna para o chamador e o progresso no método é suspenso até a tarefa aguardada ser concluída. Quando a tarefa for concluída, a execução poderá ser retomada no método.<br /><br /> Para obter um exemplo simples, consulte a seção "Métodos assíncronos" em [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md). Para obter mais informações, consulte [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md).|  
|A instrução `yield return`|Um iterador realiza uma iteração personalizada em uma coleção, como uma lista ou uma matriz. Um iterador usa a instrução [yield return](../../../csharp/language-reference/keywords/yield.md) para retornar um elemento de cada vez. Quando uma instrução `yield return` for atingida, o local atual no código será lembrado. A execução será reiniciada desse local quando o iterador for chamado na próxima vez.<br /><br /> Para obter mais informações, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).|  
|A instrução `fixed`|A instrução fixed impede que o coletor de lixo faça a realocação de uma variável móvel. Para obter mais informações, consulte [fixed](../../../csharp/language-reference/keywords/fixed-statement.md).|  
|A instrução `lock`|A instrução lock permite limitar o acesso a blocos de código a apenas um thread por vez. Para obter mais informações, consulte [lock](../../../csharp/language-reference/keywords/lock-statement.md).|  
|Instruções rotuladas|Você pode atribuir um rótulo a uma instrução e, em seguida, usar a palavra-chave [goto](../../../csharp/language-reference/keywords/goto.md) para ir diretamente para a instrução rotulada. (Veja o exemplo na linha a seguir.)|  
|A instrução vazia|A instrução vazia consiste em um único ponto e vírgula. Ela não faz nada e pode ser usada em locais em que uma instrução é necessária, mas nenhuma ação precisa ser executada. Os exemplos a seguir mostram dois usos de uma instrução vazia:<br /><br /> [!code-csharp[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]|  
  
## <a name="embedded-statements"></a>Instruções inseridas  
 Algumas instruções, inclusive [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), [for](../../../csharp/language-reference/keywords/for.md) e [foreach](../../../csharp/language-reference/keywords/foreach-in.md), sempre têm uma instrução inserida que as segue. Essa instrução inserida pode ser uma instrução única ou várias instruções entre colchetes {} em um bloco de instrução. Até mesmo instruções inseridas de uma única linha podem ser colocadas entre colchetes {}, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 Uma declaração inserida que não está entre colchetes {} não pode ser uma instrução de declaração ou uma instrução rotulada. Isso é mostrado no exemplo a seguir:  
  
 [!code-csharp[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 Coloque a instrução inserida em um bloco para corrigir o erro:  
  
 [!code-csharp[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## <a name="nested-statement-blocks"></a>Blocos de instrução aninhados  
 Blocos de instrução podem ser aninhados, conforme mostrado no código a seguir:  
  
 [!code-csharp[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## <a name="unreachable-statements"></a>Instruções inacessíveis  
 Se o compilador determinar que o fluxo de controle nunca pode atingir uma determinada instrução em nenhuma circunstância, ele produzirá o aviso CS0162, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## <a name="related-sections"></a>Seções relacionadas  
  
-   [Palavras-chave de instrução](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [Expressões](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
