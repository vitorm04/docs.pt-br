---
title: for (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 9d7ab9e37be61384c33833381f44257169c81c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="for-c-reference"></a>for (Referência de C#)
Ao usar um loop `for`, você pode executar uma instrução ou um bloco de instruções repetidamente até que uma expressão especificada seja avaliada como `false`. Esse tipo de loop é útil para a iteração em matrizes e para outras aplicações nas quais você sabe com antecedência quantas vezes deseja que o loop itere.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o valor de `i` é gravado no console e é incrementado em 1 durante cada iteração do loop.  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 A instrução `for` no exemplo anterior realiza as seguintes ações.  
  
1.  Primeiro, o valor inicial da variável `i` é estabelecido. Esta etapa ocorre apenas uma vez, independentemente de quantas vezes o loop se repete. Você pode pensar nessa inicialização como ocorrendo fora do processo de loop.  
  
2.  Para avaliar a condição (`i <= 5`), o valor de `i` é comparado com 5.  
  
    -   Se `i` é menor ou igual a 5, a condição é avaliada como `true` e ocorrem as seguintes ações.  
  
        1.  A instrução `Console.WriteLine` no corpo do loop exibe o valor de `i`.  
  
        2.  O valor de `i` é incrementado em 1.  
  
        3.  O loop retorna para o início da etapa 2 para avaliar a condição novamente.  
  
    -   Se `i` é maior que 5, a condição é avaliada como `false` e você sai do loop.  
  
 Observe que, se o valor inicial de `i` é maior que 5, o corpo do loop não é executado nenhuma vez.  
  
 Cada instrução `for` define seções de inicializador, de condição e de iterador. Essas seções geralmente determinam quantas vezes o loop vai iterar.  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 As seções atendem às seguintes finalidades.  
  
-   A seção de inicializador define as condições iniciais. As instruções nesta seção são executadas apenas uma vez, antes de entrar no loop. A seção pode conter apenas uma das duas opções a seguir.  
  
    -   A declaração e inicialização de uma variável de loop local, como mostrado no primeiro exemplo (`int i = 1`). A variável é local para o loop e não pode ser acessada de fora do loop.  
  
    -   Zero ou mais expressões de instrução da lista a seguir, separadas por vírgulas.  
  
        -   instrução de [atribuição](../../../csharp/language-reference/operators/assignment-operator.md)  
  
        -   invocação de um método  
  
        -   prefixo ou sufixo da expressão [incrementar](../../../csharp/language-reference/operators/increment-operator.md), como `++i` ou `i++`  
  
        -   prefixo ou sufixo da expressão [decrementar](../../../csharp/language-reference/operators/decrement-operator.md), como `--i` ou `i--`  
  
        -   criação de um objeto usando [new](../../../csharp/language-reference/keywords/new-operator.md)  
  
        -   expressão [await](../../../csharp/language-reference/keywords/await.md)  
  
-   A seção de condição contém uma expressão booliana que é avaliada para determinar se o loop deve sair ou deve ser executado novamente.  
  
-   A seção de iterador define o que acontece depois de cada iteração do corpo do loop. A seção de iterador contém zero ou mais das seguintes expressões de instrução, separadas por vírgulas:  
  
    -   instrução de [atribuição](../../../csharp/language-reference/operators/assignment-operator.md)  
  
    -   invocação de um método  
  
    -   prefixo ou sufixo da expressão [incrementar](../../../csharp/language-reference/operators/increment-operator.md), como `++i` ou `i++`  
  
    -   prefixo ou sufixo da expressão [decrementar](../../../csharp/language-reference/operators/decrement-operator.md), como `--i` ou `i--`  
  
    -   criação de um objeto usando [new](../../../csharp/language-reference/keywords/new-operator.md)  
  
    -   expressão [await](../../../csharp/language-reference/keywords/await.md)  
  
-   O corpo do loop consiste em uma instrução, uma instrução vazia ou um bloco de instruções que você cria colocando zero ou mais instruções entre chaves.  
  
     Você pode sair de um loop `for` usando a palavra-chave [break](../../../csharp/language-reference/keywords/break.md) ou você pode passar para a próxima iteração, usando a palavra-chave [continue](../../../csharp/language-reference/keywords/continue.md). Você também pode sair qualquer loop usando uma instrução [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).  
  
 O primeiro exemplo neste tópico mostra o tipo mais comum de loop `for`, que faz as seguintes opções para as seções.  
  
-   O inicializador declara e inicializa uma variável de loop local `i`, que mantém uma contagem das iterações do loop.  
  
-   A condição verifica o valor da variável de loop em relação a um valor final conhecido, 5.  
  
-   A seção de iterador usa uma instrução de incremento de sufixo, `i++`, para calcular cada iteração do loop.  
  
 O exemplo a seguir ilustra várias opções menos comuns: atribuir um valor a uma variável de loop externa na seção inicializador, invocar o método `Console.WriteLine` nas seções de inicializador e de iterador e alterar os valores de duas variáveis na seção de iterador.  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 Todas as expressões que definem um instrução `for` são opcionais. Por exemplo, a instrução a seguir cria um loop infinito.  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Instrução for (C++)](/cpp/cpp/for-statement-cpp)  
 [Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)
