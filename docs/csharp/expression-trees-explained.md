---
title: Árvores de Expressão Explicadas
description: Saiba mais sobre árvores de expressão e como elas são úteis em algoritmos de conversão para execução externa e inspeção do código antes de executá-lo.
ms.date: 06/20/2016
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 012ea0dec85e6fba7581f4bc46a5e78da8c64708
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481425"
---
# <a name="expression-trees-explained"></a>Árvores de Expressão Explicadas

[Anterior – Visão geral](expression-trees.md)

Uma Árvore de expressão é uma estrutura de dados que define o código. Elas se baseiam nas mesmas estruturas que um compilador usa para analisar o código e gerar a saída compilada. Ao ler este tutorial, você notará certa semelhança entre árvores de expressão e os tipos usados nas APIs Roslyn para criar [Analyzers e CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Analyzers e CodeFixes são pacotes NuGet que realizam análise estática no código e podem sugerir possíveis correções para um desenvolvedor). Os conceitos são semelhantes e o resultado final é uma estrutura de dados que permite o exame do código-fonte de uma maneira significativa. No entanto, as árvores de expressão são baseadas em um conjunto de classes e APIs totalmente diferente das APIs Roslyn.

Vejamos um exemplo simples.
Aqui está uma linha de código:

```csharp
var sum = 1 + 2;
```
Se você analisar isso como uma árvore de expressão, a árvore contém vários nós.
O nó mais externo é uma instrução de declaração de variável com atribuição (`var sum = 1 + 2;`). Esse nó mais externo contém vários nós filho: uma declaração de variável, um operador de atribuição e uma expressão que representa o lado direito do sinal de igual. Essa expressão é ainda subdividida em expressões que representam a operação de adição e os operandos esquerdo e direito da adição.

Vamos detalhar um pouco mais as expressões que compõem o lado direito do sinal de igual.
A expressão é `1 + 2`. Essa é uma expressão binária. Mais especificamente, ela é uma expressão de adição binária. Uma expressão de adição binária tem dois filhos, que representam os nós esquerdo e direito da expressão de adição. Aqui, os dois nós são expressões constantes: o operando esquerdo é o valor `1` e o operando direito é o valor `2`.

Visualmente, a declaração inteira é uma árvore: você pode começar no nó raiz e viajar até cada nó da árvore para ver o código que constitui a instrução:

- Instrução de declaração de variável com atribuição (`var sum = 1 + 2;`)
  * Declaração de tipo de variável implícita (`var sum`)
    - Palavra-chave var implícita (`var`)
    - Declaração de nome de variável (`sum`)
  * Operador de atribuição (`=`)
  * Expressão de adição binária (`1 + 2`)
    - Operando esquerdo (`1`)
    - Operador de adição (`+`)
    - Operando direito (`2`)

Isso pode parecer complicado, mas é muito eficiente. Seguindo o mesmo processo, você pode decompor expressões muito mais complicadas. Considere esta expressão:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

A expressão acima também é uma declaração de variável com uma atribuição.
Neste exemplo, o lado direito da atribuição é uma árvore muito mais complicada.
Eu não vou decompor essa expressão, mas considere quais seriam os diferentes nós. Há chamadas de método usando o objeto atual como um receptor, uma que tem um receptor `this` explicito e outra que não. Há chamadas de método usando outros objetos receptores, há argumentos constantes de tipos diferentes. E, finalmente, há um operador de adição binária. Dependendo do tipo de retorno de `SecretSauceFunction()` ou `MoreSecretSauce()`, esse operador de adição binária pode ser uma chamada de método para um operador de adição substituído, resolvendo em uma chamada de método estático ao operador de adição binária definido para uma classe.

Apesar dessa complexidade, a expressão acima cria uma estrutura de árvore que pode ser percorrida tão facilmente quanto o primeiro exemplo. Você pode continuar percorrendo os nós filho para encontrar os nós folha na expressão. Os nós pai terão referências aos filhos e cada nó tem uma propriedade que descreve o tipo de nó.

A estrutura de uma árvore de expressão é muito consistente. Depois de aprender os conceitos básicos, você poderá entender até mesmo o código mais complexo, quando ele for representado como uma árvore de expressão. A elegância na estrutura de dados explica como o compilador do C# pode analisar os programas em C# mais complexos e criar a saída apropriada desse código-fonte complicado.

Uma vez que estiver familiarizado com a estrutura das árvores de expressão, você descobrirá que o conhecimento adquirido permitirá que você trabalhe com muitos outros cenários ainda mais avançados. Há um poder incrível nas árvores de expressão.

Além de mover algoritmos para serem executados em outros ambientes, as árvores de expressão podem ser usadas para tornar mais fácil escrever algoritmos que inspecionam o código antes de executá-lo. Você pode escrever um método cujos argumentos são expressões e, em seguida, examinar essas expressões antes de executar o código. A árvore de expressão é uma representação completa do código: você pode ver os valores de qualquer subexpressão.
Você pode ver os nomes de métodos e propriedades. Você pode ver o valor de qualquer expressão de constante.
Você também pode converter uma árvore de expressão em um delegado executável e executar o código.

As APIs para árvores de expressão permitem criar árvores que representam quase todos os constructos de código válidos. No entanto, para manter as coisas o mais simples possível, algumas expressões de C# não podem ser criadas em uma árvore de expressão. Um exemplo são as expressões assíncronas (usando as palavras-chave `async` e `await`). Se suas necessidades requerem algoritmos assíncronos, você precisa manipular diretamente os objetos `Task`, em vez de contar com o suporte do compilador. Outro exemplo é na criação de loops. Normalmente, você os cria usando loops `for`, `foreach`, `while` ou `do`. Como você verá [mais adiante nesta série](expression-trees-building.md), as APIs para árvores de expressão oferecem suporte a uma única expressão de loop, com expressões `break` e `continue` que controlam a repetição do loop.

A única coisa que você não pode fazer é modificar uma árvore de expressão.  As árvores de expressão são estruturas de dados imutáveis. Se quiser modificar (alterar) uma árvore de expressão, você deverá criar uma nova árvore, que seja uma cópia da original, com as alterações desejadas.

[Próximo – Tipos de estruturas que dão suporte às árvores de expressão](expression-classes.md)
