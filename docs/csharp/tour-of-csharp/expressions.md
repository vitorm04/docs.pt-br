---
title: Expressões C# - um tour pela linguagem C#
description: expressões, operandos e operadores são blocos de compilação da linguagem C#
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4ffe947a4cb8c36a5925a4b3846486e44a9d8ec4
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480749"
---
# <a name="expressions"></a>Expressões

*Expressões* são construídas a partir de *operandos* e *operadores*. Os operadores de uma expressão indicam quais operações devem ser aplicadas aos operandos. Exemplos de operadores incluem `+`, `-`, `*`, `/` e `new`. Exemplos de operandos incluem literais, campos, variáveis locais e expressões.

Quando uma expressão contiver vários operadores, a *precedência* dos operadores controla a ordem na qual os operadores individuais são avaliados. Por exemplo, a expressão `x + y * z` é avaliada como `x + (y * z)` porque o operador `*` tem precedência maior do que o operador `+`.

Quando ocorre um operando entre dois operadores com a mesma precedência, a *associatividade* dos operadores controla a ordem na qual as operações são executadas:

* Exceto para os operadores de atribuição, todos os operadores binários são *associativos à esquerda*, o que significa que as operações são executadas da esquerda para a direita. Por exemplo, `x + y + z` é avaliado como `(x + y) + z`.
* Os operadores de atribuição e o operador condicional (`?:`) são *associativos à direita*, o que significa que as operações são executadas da direita para a esquerda. Por exemplo, `x = y = z` é avaliado como `x = (y = z)`.

Precedência e associatividade podem ser controladas usando parênteses. Por exemplo, `x + y * z` primeiro multiplica `y` por `z` e, em seguida, adiciona o resultado a `x`, mas `(x + y) * z` primeiro adiciona `x` e `y` e, em seguida, multiplica o resultado por `z`.

A maioria dos operadores pode ser *sobrecarregada*. A sobrecarga de operador permite que implementações de operador definidas pelo usuário sejam especificadas para operações em que um ou ambos os operandos são de um tipo struct ou de classe definida pelo usuário.

O item a seguir resume os operadores do C#, listando as categorias de operador em ordem de precedência da mais alta para a mais baixa. Operadores na mesma categoria têm a mesma precedência. Em cada categoria está uma lista de expressões da categoria juntamente com a descrição do tipo de expressão.

* Primária
  - `x.m`: Acesso de membros
  - `x(...)`: Invocação de método e delegado
  - `x[...]`: Acesso de matriz e indexador
  - `x++`: Pós-incremento
  - `x--`: Pós-decremento
  - `new T(...)`: Criação de objeto e delegado
  - `new T(...){...}`: Criação de objeto com inicializador
  - `new {...}`:  Inicializador de objeto anônimo
  - `new T[...]`: Criação de matriz
  - `typeof(T)`: Obter objeto <xref:System.Type> para `T`
  - `checked(x)`: Avalia expressão no contexto selecionado
  - `unchecked(x)`: Avalia expressão no contexto desmarcado
  - `default(T)`: Obter valor padrão do tipo `T`
  - `delegate {...}`: Função anônima (método anônimo)
* Unário
  - `+x`: Identidade
  - `-x`: Negação
  - `!x`: Negação lógica
  - `~x`: Negação bit a bit
  - `++x`: Pré-incremento
  - `--x`: Pré-decremento
  - `(T)x`: Converter explicitamente `x` no tipo `T`
  - `await x`: Aguardar assincronamente `x` para concluir
* Multiplicativo
  - `x * y`: Multiplicação
  - `x / y`: Divisão
  - `x % y`: Restante
* Aditivo
  - `x + y`: Adição, concatenação de cadeia de caracteres, combinação de delegados
  - `x – y`: Subtração, remoção de delegado
* Shift
  - `x << y`: Shift esquerdo
  - `x >> y`: Shift direito
* Teste de tipo e relacional
  - `x < y`: Menor que
  - `x > y`: Maior que
  - `x <= y`: Menor ou igual a
  - `x >= y`: Maior que ou igual a
  - `x is T`: Retorna `true` se `x` for um `T`, caso contrário, `false`
  - `x as T`: Retorna `x` digitado como `T` ou `null`, se `x` não for um `T`
* Igualdade
  - `x == y`: Igual a
  - `x != y`: Diferente de
* AND lógico
  - `x & y`: AND bit a bit inteiro, AND lógico booliano
* XOR lógico
  - `x ^ y`: XOR bit a bit inteiro, XOR lógico booliano
* OR lógico
  - `x | y`: OR bit a bit inteiro, OR lógico booliano
* AND condicional
  - `x && y`: Avalia `y` somente se `x` não for `false`
* OR condicional
  - `x || y`: Avalia `y` somente se `x` não for `true`
* Coalescência nula
  - `x ?? y`: Avalia como `y` se `x` for nulo, caso contrário, como `x`
* Condicional
  - `x ? y : z`: Avalia `y` se `x` for `true`, `z` se `x` for `false`
* Atribuição ou função anônima
  - `x = y`: Atribuição
  - `x op= y`: Atribuição composta; operadores com suporte
    - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
  - `(T x) => y`: Função anônima (expressão lambda)

> [!div class="step-by-step"]
> [Anterior](types-and-variables.md)
> [Próximo](statements.md)
