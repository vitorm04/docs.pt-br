---
title: for (Referência de C#)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207842"
---
# <a name="for-c-reference"></a>for (referência de C#)

A instrução `for` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.

Em qualquer ponto dentro do bloco de instrução `for`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md). Você também pode sair de um loop `for` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).
  
## <a name="structure-of-the-for-statement"></a>Estrutura da instrução `for`

A instrução `for` define as seções *Inicializador*, *Condição* e *Iterador*:
  
```csharp
for (initializer; condition; iterator)  
    body  
```

Todas as três seções são opcionais. O corpo do loop é uma instrução ou um bloco de instruções.

A exemplo a seguir mostra a instrução `for` com todas as seções definidas:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>A seção *Inicializador*

As instruções na seção *Inicializador* são executadas apenas uma vez, antes de entrar no loop. A seção *Inicializador* é uma das seguintes:

- A declaração e a inicialização de uma variável de loop local, que não pode ser acessada de fora do loop.

- Zero ou mais expressões de instrução da lista a seguir, separadas por vírgulas:

  - instrução de [atribuição](../operators/assignment-operator.md)

  - invocação de um método  

  - prefixo ou sufixo da expressão [incrementar](../operators/increment-operator.md), como `++i` ou `i++`  

  - prefixo ou sufixo da expressão [decrementar](../operators/decrement-operator.md), como `--i` ou `i--`  

  - criação de um objeto usando a palavra-chave [novo](new-operator.md)

  - expressão [await](await.md)

A seção *Inicializador* no exemplo acima declara e inicializa a variável de loop local `i`:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>A seção *Condição*

A seção *Condição*, se presente, deverá ser uma expressão booliana. Essa expressão é avaliada antes de cada iteração do loop. Se a seção *Condição* não estiver presente ou a expressão booliana for avaliada como `true`, a próxima iteração do loop será executada; caso contrário, o loop será finalizado.

A seção *Condição* no exemplo acima determina se o loop será encerrado com base no valor da variável de loop local:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>A seção *Iterador*

A seção *Iterador* define o que acontece depois de cada iteração do corpo do loop. A seção *Iterador* contém zero ou mais das seguintes expressões de instrução, separadas por vírgulas:  

- instrução de [atribuição](../operators/assignment-operator.md)

- invocação de um método  

- prefixo ou sufixo da expressão [incrementar](../operators/increment-operator.md), como `++i` ou `i++`  

- prefixo ou sufixo da expressão [decrementar](../operators/decrement-operator.md), como `--i` ou `i--`  

- criação de um objeto usando a palavra-chave [novo](new-operator.md)

- expressão [await](await.md)

A seção *Iterador* no exemplo acima incrementa a variável de loop local:

```csharp
i++
```

## <a name="examples"></a>Exemplos

O exemplo a seguir ilustra vários usos menos comuns das seções de instrução `for`: atribuir um valor a uma variável de loop externa na seção *Inicializador*, invocar um método inicializa nas seções *Inicializador* e *Iterador* e alterar os valores de duas variáveis na seção *Iterador*. Selecione **Executar** para executar o código de exemplo. Depois disso, você pode modificar o código e executá-lo novamente.
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
O exemplo a seguir define o loop `for` infinito:
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a>especificação da linguagem C#  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a>Consulte também

[A instrução for (especificação da linguagem C#)](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[Referência de C#](../index.md)  
[Guia de Programação em C#](../../programming-guide/index.md)  
[Palavras-chave do C#](index.md)  
[foreach, in](foreach-in.md)  
[Instrução for (C++)](/cpp/cpp/for-statement-cpp)  
[Instruções de iteração](iteration-statements.md)
