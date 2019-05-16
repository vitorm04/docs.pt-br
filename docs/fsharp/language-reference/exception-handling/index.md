---
title: Tratamento de Exceção
description: Conheça os fundamentos do tratamento de exceção no F# e encontre links para expressões e funções de manipulação de exceção.
ms.date: 05/16/2016
ms.openlocfilehash: 0f4e57bfd643cba3dab5281df484ebb6162cb4b7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645473"
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
|[Exceções: O `try...with` expressão](the-try-with-expression.md)|Descreve a construção de linguagem que oferece suporte à manipulação da exceção.|
|[Exceções: O `try...finally` expressão](the-try-finally-expression.md)|Descreve a construção de linguagem que permite a execução do código de limpeza conforme a pilha é liberada quando uma exceção é lançada.|
|[Exceções: a função `raise`](the-raise-Function.md)|Descreve como lançar um objeto de exceção.|
|[Exceções: O `failwith` função](the-failwith-function.md)|Descreve como gerar uma exceção geral do F#.|
|[Exceções: O `invalidArg` função](the-invalidArg-function.md)|Descreve como gerar uma exceção de argumento inválido.|
