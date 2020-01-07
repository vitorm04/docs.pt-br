---
title: Ordenação
ms.date: 12/13/2019
description: Saiba como criar uma sequência de Agrupamento Personalizada.
ms.openlocfilehash: 0942ad4523a149ad74321cbe0f63021f53303579
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447023"
---
# <a name="collation"></a>Ordenação

As sequências de agrupamento são usadas pelo SQLite ao comparar valores de texto para determinar a ordem e a igualdade. Você pode especificar qual Agrupamento usar ao criar colunas ou por operação em consultas SQL. O SQLite inclui três sequências de agrupamento por padrão.

| Ordenação | Descrição                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignora o espaço em branco à direita               |
| NOCASESEMMAIÚSCMINÚSC    | Não diferencia maiúsculas de minúsculas para caracteres ASCII de A-Z |
| BINARY    | Diferenciar maiúsculas de minúsculas. Compara bytes diretamente   |

## <a name="custom-collation"></a>Agrupamento personalizado

Você também pode definir suas próprias sequências de agrupamento ou substituir as internas usando <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>. O exemplo a seguir mostra a substituição do agrupamento nocase para dar suporte a caracteres Unicode. O [código de exemplo completo](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) está disponível no github.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Operador Like

O operador LIKE no SQLite não honra agrupamentos. A implementação padrão tem a mesma semântica que o agrupamento nocase. É apenas não diferencia maiúsculas de minúsculas para os caracteres ASCII de a a Z.

Você pode facilmente tornar o operador LIKE com diferenciação de maiúsculas e minúsculas usando a seguinte instrução pragma:

```sql
PRAGMA case_sensitive_like = 0
```

Consulte [funções definidas pelo usuário](user-defined-functions.md) para obter detalhes sobre como substituir a implementação do operador Like.

## <a name="see-also"></a>Veja também

* [Funções definidas pelo usuário](user-defined-functions.md)
* [Sintaxe SQL](https://www.sqlite.org/lang.html)
