---
title: Expressões C# - um tour pela linguagem C#
description: expressões, operandos e operadores são blocos de compilação da linguagem C#
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 8fa1c5d0464644b26eb457bca8ecaf007c288f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="expressions"></a>Expressões

*Expressões* são construídas a partir de *operandos* e *operadores*. Os operadores de uma expressão indicam quais operações devem ser aplicadas aos operandos. Exemplos de operadores incluem `+`, `-`, `*`, `/` e `new`. Exemplos de operandos incluem literais, campos, variáveis locais e expressões.

Quando uma expressão contiver vários operadores, a *precedência* dos operadores controla a ordem na qual os operadores individuais são avaliados. Por exemplo, a expressão `x + y * z` é avaliada como `x + (y * z)` porque o operador `*` tem precedência maior do que o operador `+`.

Quando ocorre um operando entre dois operadores com a mesma precedência, a *associatividade* dos operadores controla a ordem na qual as operações são executadas:

*   Exceto para os operadores de atribuição, todos os operadores binários são *associativos à esquerda*, o que significa que as operações são executadas da esquerda para a direita. Por exemplo, `x + y + z` é avaliado como `(x + y) + z`.
*   Os operadores de atribuição e o operador condicional (`?:`) são *associativos à direita*, o que significa que as operações são executadas da direita para a esquerda. Por exemplo, `x = y = z` é avaliado como `x = (y = z)`.

Precedência e associatividade podem ser controladas usando parênteses. Por exemplo, `x + y * z` primeiro multiplica `y` por `z` e, em seguida, adiciona o resultado a `x`, mas `(x + y) * z` primeiro adiciona `x` e `y` e, em seguida, multiplica o resultado por `z`.

A maioria dos operadores pode ser *sobrecarregada*. A sobrecarga de operador permite que implementações de operador definidas pelo usuário sejam especificadas para operações em que um ou ambos os operandos são de um tipo struct ou de classe definida pelo usuário.

O item a seguir resume os operadores do C#, listando as categorias de operador em ordem de precedência da mais alta para a mais baixa. Operadores na mesma categoria têm a mesma precedência. Em cada categoria está uma lista de expressões da categoria juntamente com a descrição do tipo de expressão.

* Primária
    - `x.m`: acesso de membro
    - `x(...)`: invocação de método e delegado
    - `x[...]`: acesso de matriz e indexador
    - `x++`: pós-incremento
    - `x--`: pós-decremento
    - `new T(...)`: criação de objeto e delegado
    - `new T(...){...}`: criação de objeto com inicializador
    - `new {...}`: inicializador de objeto anônimo
    - `new T[...]`: criação de matriz
    - `typeof(T)`: obter objeto <xref:System.Type> para `T`
    - `checked(x)`: avaliar expressão no contexto marcado
    - `unchecked(x)`: avaliar expressão no contexto desmarcado
    - `default(T)`: obter valor padrão do tipo `T`
    - `delegate {...}`: função anônima (método anônimo)
* Unário
    - `+x`: identidade
    - `-x`: negação
    - `!x`: negação lógica
    - `~x`: negação bit a bit
    - `++x`: pré-incremento
    - `--x`: pré-decremento
    - `(T)x`: converter explicitamente `x` no tipo `T`
    - `await x`: aguardar assincronamente `x` para concluir
* Multiplicativo
    - `x * y`: multiplicação
    - `x / y`: divisão
    - `x % y`: resto
* Aditivo
    - `x + y`: adição, concatenação de cadeia de caracteres, combinação de delegados
    - `x – y`: subtração, remoção de delegado
* Shift
    - `x << y`: Shift esquerdo
    - `x >> y`: Shift direito
* Teste de tipo e relacional
    - `x < y`: é menor que
    - `x > y`: é maior que
    - `x <= y`: é menor que ou igual a
    - `x >= y`: é maior que ou igual a
    - `x is T`: retornará `true` se `x` for um `T`, caso contrário, `false`
    - `x as T`: retornará `x` digitado como `T` ou `null` se `x` não for um `T`
* Igualdade
    - `x == y`: igual a
    - `x != y`: não é igual a
* AND lógico
    - `x & y`: AND bit a bit inteiro, AND lógico booliano
* XOR lógico
    - `x ^ y`: XOR bit a bit inteiro, XOR lógico booliano
* OR lógico
    - `x | y`: OR bit a bit inteiro, OR lógico booliano
* AND condicional
    - `x && y`: avaliará `y` somente se `x` não for `false`
* OR condicional
    - `x || y`: avaliará `y` somente se `x` não for `true`
* Coalescência nula
    - `x ?? y`: avaliará como `y` se `x` for nulo, caso contrário, como `x`
* Condicional
    - `x ? y : z`: avaliará `y` se `x` for `true`, `z` se `x` for `false`
* Atribuição ou função anônima
    - `x = y`: atribuição
    - `x op= y`: atribuição composta; operadores com suporte
        - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
    - `(T x) => y`: função anônima (expressão lambda)

>[!div class="step-by-step"]
[Anterior](types-and-variables.md)
[Próximo](statements.md)
