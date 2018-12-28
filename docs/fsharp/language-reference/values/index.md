---
title: Valores
description: Saiba como os valores em F# são as quantidades que têm um tipo específico.
ms.date: 05/16/2016
ms.openlocfilehash: 5c1d4f1e59cbf092911d99a725654042bf3383b1
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611874"
---
# <a name="values"></a>Valores

Os valores em F# podem ser números inteiros ou de ponto flutuante, caracteres ou texto, listas, sequências, matrizes, tuplas, uniões discriminadas, registros, tipos de classe ou valores de função.

## <a name="binding-a-value"></a>Associação de valor

O termo *associação* significa associar um nome a uma definição. A palavra-chave `let` associa um valor, como nos exemplos a seguir:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

O tipo de um valor é inferido da definição. Para um tipo primitivo, como um número de ponto flutuante ou integral, o tipo é determinado pelo tipo do literal. Portanto, no exemplo anterior, o compilador infere o tipo de `b` como `unsigned int`, enquanto o compilador infere o tipo de `a` como `int`. O tipo de valor de uma função é determinado pelo valor de retorno no corpo da função. Para saber mais sobre tipos de valor de função, veja [Funções](../functions/index.md). Para saber mais sobre tipos de literal, veja [Literais](../literals.md).

O compilador não emite diagnóstico sobre associações não utilizados por padrão. Para receber essas mensagens, habilitar o aviso 1182 no arquivo de projeto ou ao invocar o compilador (consulte `--warnon` sob [opções do compilador](../compiler-options.md)).

## <a name="why-immutable"></a>Por que imutável?

Valores imutáveis são valores que não podem ser alterados durante a execução de um programa. Se você estiver acostumado com linguagens como C++, Visual Basic ou X#, talvez se surpreenda por F# dar prioridade para valores imutáveis em vez de variáveis que podem receber novos valores durante a execução de um programa. Dados imutáveis são um elemento importante da programação funcional. Em um ambiente multithread, é difícil gerenciar variáveis mutáveis compartilhadas que podem ser alteradas por muitos threads diferentes. Além disso, com as variáveis mutáveis, às vezes pode ser difícil dizer se uma variável pode ser alterada quando ela é passada para outra função.

Em linguagens funcionais puras, não há variáveis, e as funções se comportam estritamente como funções matemáticas. Quando um código em uma linguagem de procedimento usa uma atribuição de variável para alterar um valor, o código equivalente em uma linguagem funcional tem um valor imutável, que é a entrada, uma função imutável e valores imutáveis diferentes como saída. Essa limitação matemática permite uma raciocínio mais firme sobre o comportamento do programa. Esse raciocínio mais firme é o que permite aos compiladores verificar o código de forma mais rigorosa e otimizar com mais efetividade, além de ajudar os desenvolvedores a entender e a escrever o código corretamente. Portanto, provavelmente o código funcional é mais fácil de depurar do que o código de procedimento comum.

F# não é uma linguagem funcional pura, ainda assim é totalmente compatível com a programação funcional. O uso de valores imutáveis é uma prática recomendada, pois isso permite que seu código se beneficie de um aspecto importante da programação funcional.

## <a name="mutable-variables"></a>Variáveis mutáveis

Você pode usar a palavra-chave `mutable` para especificar uma variável que pode ser alterada. As variáveis mutáveis em F# geralmente devem ter um escopo limitado, como um campo de um tipo ou um valor local. Variáveis mutáveis com um escopo limitado são mais fáceis de controlar e têm uma probabilidade menor de serem modificadas de maneira incorreta.

Você pode atribuir um valor inicial para uma variável mutável usando a palavra-chave `let` da mesma maneira que você definira um valor. No entanto, a diferença é que você pode atribuir posteriormente novos valores a variáveis mutáveis usando o operador `<-`, como no exemplo a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

Os valores marcados `mutable` pode ser elevada automaticamente a `'a ref` se capturadas por um fechamento, incluindo formulários que criar fechamentos, tais como `seq` construtores. Se você quiser ser notificado quando isso ocorre, habilitar o aviso 3180 no arquivo de projeto ou ao invocar o compilador.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----|-----------|
|[Associações let](../functions/let-bindings.md)|Fornece informações sobre como usar o `let` palavra-chave para associar nomes a valores e funções.|
|[Funções](../functions/index.md)|Fornece uma visão geral das funções em F#.|

## <a name="see-also"></a>Consulte também

- [Valores Nulos](null-Values.md)
- [Referência da Linguagem F#](../index.md)