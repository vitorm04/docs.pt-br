---
title: Tratamento de Exceção
description: Conheça os conceitos básicos do tratamento de F# exceções no e encontre links para expressões e funções de tratamento de exceções.
ms.date: 05/16/2016
ms.openlocfilehash: e34a65dd7da9d706153254ac28e729de0745e4d0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423066"
---
# <a name="exception-handling"></a>Tratamento de Exceção

Esta seção contém informações sobre suporte à manipulação de exceção na linguagem F#.

## <a name="exception-handling-basics"></a>Noções básicas do tratamento de exceção

O tratamento de exceção é a maneira padrão de lidar com condições de erro no .NET Framework. Portanto, qualquer linguagem .NET deve oferecer suporte a esse mecanismo, incluindo F#. Um *exceção* é um objeto que encapsula informações sobre um erro. Quando ocorrem erros, as exceções são acionadas e a execução normal é interrompida. Em vez disso, o tempo de execução procura um manipulador apropriado para a exceção. A pesquisa começa na função atual e continua na pilha passando pelas camadas de chamadores até que um manipulador correspondente é encontrado. Em seguida, o manipulador é executado.

Além disso, à medida que a pilha é liberada, o tempo de execução executa qualquer código nos blocos `finally` para garantir que os objetos sejam limpos corretamente durante o processo de liberação.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----|-----------|
|[Tipos de Exceção](exception-types.md)|Descreve como declarar um tipo de exceção.|
|[Exceções: a expressão `try...with`](the-try-with-expression.md)|Descreve a construção de linguagem que oferece suporte à manipulação da exceção.|
|[Exceções: a expressão `try...finally`](the-try-finally-expression.md)|Descreve a construção de linguagem que permite a execução do código de limpeza conforme a pilha é liberada quando uma exceção é lançada.|
|[Exceções: a função `raise`](the-raise-Function.md)|Descreve como lançar um objeto de exceção.|
|[Exceções: a função `failwith`](the-failwith-function.md)|Descreve como gerar uma exceção geral do F#.|
|[Exceções: a função `invalidArg`](the-invalidArg-function.md)|Descreve como gerar uma exceção de argumento inválido.|
