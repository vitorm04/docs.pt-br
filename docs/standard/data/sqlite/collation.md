---
title: Collation
ms.date: 12/13/2019
description: Aprenda a criar uma seqüência de colagem personalizada.
ms.openlocfilehash: b93c82a4ace154b8293b05effa8f9e9294fa7708
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506535"
---
# <a name="collation"></a>Collation

As seqüências de coletâneas são usadas pelo SQLite ao comparar valores de TEXTO para determinar a ordem e a igualdade. Você pode especificar qual colagem usar ao criar colunas ou por operação em consultas SQL. O SQLite inclui três seqüências de colisão por padrão.

| Collation | Descrição                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignora o espaço branco em arrasto               |
| NOCASE    | Caso insensível para caracteres ASCII A-Z |
| BINARY    | Sensível a casos. Compara bytes diretamente   |

## <a name="custom-collation"></a>Colagem personalizada

Você também pode definir suas próprias seqüências de colisão ou substituir as incorporadas usando <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>. O exemplo a seguir mostra sobrepondo a colagem NOCASE para suportar caracteres Unicode. O [código de amostra completo](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) está disponível no GitHub.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Operador Like

O operador LIKE no SQLite não honra colagens. A implementação padrão tem a mesma semântica que a colagem NOCASE. É apenas caso insensível para os caracteres ASCII de A a Z.

Você pode facilmente tornar o operador LIKE sensível ao caso usando a seguinte declaração pragma:

```sql
PRAGMA case_sensitive_like = 1
```

Consulte [as funções definidas pelo usuário](user-defined-functions.md) para obter detalhes sobre a substituição da implementação do operador LIKE.

## <a name="see-also"></a>Confira também

* [Funções definidas pelo usuário](user-defined-functions.md)
* [Sintaxe SQL](https://www.sqlite.org/lang.html)
