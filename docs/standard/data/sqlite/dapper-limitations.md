---
title: Limitações do Dapper
ms.date: 12/13/2019
description: Descreve algumas das limitações que você encontrará ao usar o Dapper.
ms.openlocfilehash: 90c7fb24f068d663081390bdba9b1b222b4be56e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447275"
---
# <a name="dapper-limitations"></a>Limitações do Dapper

Há algumas limitações que você deve conhecer ao usar o Microsoft. Data. sqlite com [Dapper](https://stackexchange.github.io/Dapper/).

## <a name="parameters"></a>Parâmetros

Os nomes de parâmetro do SQLite diferenciam maiúsculas de minúsculas. Verifique se os nomes de parâmetro usados no SQL correspondem ao caso das propriedades do objeto anônimo. O problema [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) melhoraria essa experiência.

Dapper também espera parâmetros para usar o prefixo `@`. Outros prefixos não funcionarão.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a>Tipos de dados

Dapper lê os valores usando o indexador SqliteDataReader. O tipo de retorno desse indexador é Object, o que significa que ele nunca retornará valores Long, Double, String ou byte []. Para obter mais informações, consulte [tipos de dados](types.md). O Dapper lida com a maioria das conversões entre esses e outros tipos primitivos. Infelizmente, ele não lida com `DateTimeOffset`, `Guid`ou `TimeSpan`. Crie manipuladores de tipo se você quiser usar esses tipos em seus resultados.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

Não se esqueça de adicionar os manipuladores de tipo antes de consultar.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a>Veja também

* [Tipos de dados](types.md)
* [Limitações assíncronas](async.md)
