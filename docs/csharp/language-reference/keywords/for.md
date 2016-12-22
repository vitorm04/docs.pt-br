---
title: "for (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "for"
  - "for_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave for [C#]"
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: 39
caps.handback.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# for (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usando um loop de `for` , você pode executar uma instrução ou um bloco de instruções repetidamente até que uma expressão especificada classifique a `false`.  Esse tipo do loop é útil para iterar sobre matrizes e para outros aplicativos em que você sabe com antecedência quantas vezes você deseja que o loop para iterar.  
  
## Exemplo  
 Em o exemplo, o valor de `i` é escrito no console e incrementado por 1 durante cada iteração do loop.  
  
 [!code-cs[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 A declaração de `for` no exemplo anterior executa as seguintes ações.  
  
1.  Primeiro, o valor inicial de `i` variável é estabelecida.  Esta etapa acontecerá somente uma vez, independentemente de quantas vezes o loop para repetir.  Você pode pensar em essa inicialização como fora de processo aconteça o loop.  
  
2.  Para classificar uma condição`i <= 5`\(\), o valor de `i` é comparado a 5.  
  
    -   Se `i` é menor ou igual a 5, a condição avalia a `true`, e as seguintes ações ocorrer.  
  
        1.  A declaração de `Console.WriteLine` o corpo do loop exibe o valor de `i`.  
  
        2.  o valor de `i` é incrementado por 1.  
  
        3.  O loop retorna para o início da etapa 2 para avaliar novamente a condição.  
  
    -   Se `i` é maior que 5, a condição avalia a `false`, e você sai do loop.  
  
 Observe que, se o valor inicial de `i` é maior que 5, o corpo de loop não executa mesmo uma vez.  
  
 Cada declaração de `for` define o inicializador, a condição, e seções de iterador.  Essas seções geralmente determinam quantas vezes o loop itera.  
  
```c#  
for (initializer; condition; iterator)  
    body  
```  
  
 As seções a seguir servem as finalidades.  
  
-   A seção de inicializador define as condições iniciais.  As instruções em esta seccionam a execução somente uma vez, antes que você insira o loop.  A seção pode conter apenas uma das seguintes opções.  
  
    -   A declaração e a inicialização de uma variável de lacete local, como o primeiro exemplo mostra`int i = 1`\(\).  A variável é local para o loop e não pode ser acessado fora do loop.  
  
    -   Zero ou mais expressons da instrução na lista, separada por vírgulas.  
  
        -   declaração de[atribuição](../../../csharp/language-reference/operators/assignment-operator.md)  
  
        -   chamada de um método  
  
        -   prefixe ou pós\-fixar a expressão de [incremento](../../../csharp/language-reference/operators/increment-operator.md) , como `++i` ou `i++`  
  
        -   prefixe ou pós\-fixar a expressão de [redução](../../../csharp/language-reference/operators/decrement-operator.md) , como `--i` ou `i--`  
  
        -   criando um objeto usando [novo](../../../visual-basic/language-reference/operators/new-operator.md)  
  
        -   expressão de[espere](../../../csharp/language-reference/keywords/await.md)  
  
-   A seção da condição contém uma expressão booleana que é avaliada para determinar se o loop deve sair ou deve executar novamente.  
  
-   A seção de iterador define o que acontece depois cada iteração do corpo do loop.  A seção de iterador contém zero ou mais das expressões de declaração, separados por vírgulas:  
  
    -   declaração de[atribuição](../../../csharp/language-reference/operators/assignment-operator.md)  
  
    -   chamada de um método  
  
    -   prefixe ou pós\-fixar a expressão de [incremento](../../../csharp/language-reference/operators/increment-operator.md) , como `++i` ou `i++`  
  
    -   prefixe ou pós\-fixar a expressão de [redução](../../../csharp/language-reference/operators/decrement-operator.md) , como `--i` ou `i--`  
  
    -   criando um objeto usando [novo](../../../visual-basic/language-reference/operators/new-operator.md)  
  
    -   expressão de[espere](../../../csharp/language-reference/keywords/await.md)  
  
-   O corpo do loop consiste em uma instrução, uma instrução vazia, ou um bloco de instruções que você cria, incluindo zero ou mais declarações em chaves.  
  
     Você pode quebrar de um loop de `for` usando a palavra\-chave de [interrupção](../../../csharp/language-reference/keywords/break.md) , ou você pode ir para a próxima iteração usando a palavra\-chave de [continue](../../../csharp/language-reference/keywords/continue.md) .  Você também pode deixar qualquer loop usando [goto](../../../csharp/language-reference/keywords/goto.md), [retorno](../../../csharp/language-reference/keywords/return.md), ou a declaração de [throw](../../../csharp/language-reference/keywords/throw.md) .  
  
 O primeiro exemplo de este tópico mostra o tipo mais comum de loop de `for` , que faz as seguintes opções para seções.  
  
-   O inicializador declara e inicializa uma variável de lacete local, `i`, que mantém uma contagem de iterações do loop.  
  
-   As verificações de condição o valor da variável do loop com um valor final conhecido, 5.  
  
-   A seção de iterador usa uma instrução de incremento de pós\-fixação, `i++`, registrar cada iteração do loop.  
  
 O exemplo a seguir ilustra várias opções menos comuns: atribuindo um valor a uma variável externa do loop na seção de inicializador, chamar o método de `Console.WriteLine` no inicializador e nas seções de iterador, e alterar os valores de duas variáveis na seção de iterador.  
  
 [!code-cs[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 todas as expressões que definem uma instrução de `for` são opcionais.  Por exemplo, a seguinte declaração cria um loop infinito.  
  
 [!code-cs[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Instrução for \(C\+\+\)](/visual-cpp/cpp/for-statement-cpp)   
 [Instruções de iteração](../../../csharp/language-reference/keywords/iteration-statements.md)