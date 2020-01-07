---
title: Funções definidas pelo usuário
ms.date: 12/13/2019
description: Saiba como criar funções escalares e de agregação definidas pelo usuário.
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447170"
---
# <a name="user-defined-functions"></a>Funções definidas pelo usuário

A maioria dos bancos de dados tem um dialeto de procedimento do SQL que você pode usar para definir suas próprias funções. No entanto, o SQLite é executado em processo com seu aplicativo. Em vez de ter que aprender um novo dialeto do SQL, você pode usar apenas a linguagem de programação do seu aplicativo.

## <a name="scalar-functions"></a>Funções escalares

As funções escalares retornam um valor escalar único para cada linha em uma consulta. Defina novas funções escalares e substitua as internas usando <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.

Consulte [tipos de dados](types.md) para obter uma lista de parâmetros com suporte e tipos de retorno para o argumento `func`.

A especificação do argumento `state` passará esse valor para cada invocação da função. Use isso para evitar fechamentos.

Especifique `isDeterministic` se sua função for determinística para permitir que o SQLite use otimizações adicionais ao compilar consultas.

O exemplo a seguir mostra como adicionar uma função escalar para calcular o raio de um cilindro.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a>Operadores

Os seguintes operadores SQLite são implementados pelas funções escalares correspondentes. Definir essas funções escalares em seu aplicativo substituirá o comportamento desses operadores.

| Operador          | Função      |
| ----------------- | ------------- |
| X GLOB Y          | Glob (Y, X)    |
| X COMO Y          | Like (Y, X)    |
| X COMO Y ESCAPE Z | Like (Y, X, Z) |
| X CORRESPONDÊNCIA Y         | corresponder (Y, X)   |
| X REGEXP Y        | RegExp (Y, X)  |

O exemplo a seguir mostra como definir a função RegExp para habilitar seu operador correspondente. O SQLite não inclui uma implementação padrão da função RegExp.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a>Funções de Agregação

As funções de agregação retornam um valor agregado único para todas as linhas em uma consulta. Definir e substituir funções de agregação usando <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.

O argumento `seed` especifica o estado inicial do contexto. Use isso para evitar fechamentos também.

O argumento `func` é invocado uma vez por linha. Use o contexto para acumular um resultado final. Retornar o contexto. Esse padrão permite que o contexto seja um tipo de valor ou imutável.

Se nenhum `resultSelector` for especificado, o estado final do contexto será usado como resultado. Isso pode simplificar a definição de funções como Sum e Count que precisam apenas incrementar um número cada linha e retorná-la.

Especifique `resultSelector` para calcular o resultado final do contexto depois de iterar por todas as linhas.

Consulte [tipos de dados](types.md) para obter uma lista de tipos de parâmetro com suporte para o argumento `func` e tipos de retorno para `resultSelector`.

Se sua função for determinística, especifique `isDeterministic` para permitir que o SQLite use otimizações adicionais ao compilar consultas.

O exemplo a seguir define uma função de agregação para calcular o desvio padrão de uma coluna.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a>Erros do

Se uma função definida pelo usuário lançar uma exceção, a mensagem será retornada para o SQLite. O SQLite irá gerar um erro e o Microsoft. Data. sqlite gerará um Sqliteexception. Para obter mais informações, consulte [erros de banco de dados](database-errors.md).

Por padrão, o código de erro do SQLite de erro será SQLITE_ERROR (ou 1). No entanto, você pode alterá-lo lançando um <xref:Microsoft.Data.Sqlite.SqliteException> em sua função com o <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> desejado especificado.

## <a name="debugging"></a>{1&gt;Depuração&lt;1}

O SQLite chama sua implementação diretamente. Isso permite que você adicione pontos de interrupção que disparam enquanto o SQLite está avaliando consultas. A experiência completa de depuração do .NET está disponível para ajudá-lo a criar suas funções definidas pelo usuário.

## <a name="see-also"></a>Veja também

* [Tipos de dados](types.md)
* [Funções principais do SQLite](https://www.sqlite.org/lang_corefunc.html)
* [Funções de agregação do SQLite](https://www.sqlite.org/lang_aggfunc.html)
