---
title: Transações
ms.date: 12/13/2019
description: Saiba como usar transações.
ms.openlocfilehash: 4b72a1573a560ffd1bfd0f54d46ab3b135280976
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447135"
---
# <a name="transactions"></a>Transações

As transações permitem agrupar várias instruções SQL em uma única unidade de trabalho confirmada no banco de dados como uma unidade atômica. Se qualquer instrução na transação falhar, as alterações feitas pelas instruções anteriores poderão ser revertidas. O estado inicial do banco de dados quando a transação foi iniciada é preservado. O uso de uma transação também pode melhorar o desempenho no SQLite ao fazer inúmeras alterações no banco de dados ao mesmo tempo.

## <a name="concurrency"></a>Concorrência

No SQLite, somente uma transação tem permissão para ter alterações pendentes no banco de dados de cada vez. Por isso, as chamadas para <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> e os métodos `Execute` em <xref:Microsoft.Data.Sqlite.SqliteCommand> podem atingir o tempo limite se outra transação demorar muito para ser concluída.

Para obter mais informações sobre bloqueio, novas tentativas e tempos limite, consulte [erros de banco de dados](database-errors.md).

## <a name="isolation-levels"></a>Níveis de isolamento

As transações são **serializáveis** por padrão no SQLite. Esse nível de isolamento garante que todas as alterações feitas em uma transação sejam completamente isoladas. Outras instruções executadas fora da transação não são afetadas pelas alterações da transação.

O SQLite também dá suporte à **leitura não confirmada** ao usar um cache compartilhado. Esse nível permite leituras sujas, leituras não repetíveis e fantasmas:

- Uma *leitura suja* ocorre quando as alterações pendentes em uma transação são retornadas por uma consulta fora da transação, mas as alterações na transação são revertidas. Os resultados contêm dados que jamais foram realmente confirmados no banco de dados.

- Uma *leitura não reproduzível* ocorre quando uma transação consulta a mesma linha duas vezes, mas os resultados são diferentes porque foram alterados entre as duas consultas por outra transação.

- *Fantasmas* são linhas que são alteradas ou adicionadas para atender à cláusula WHERE de uma consulta durante uma transação. Se permitido, a mesma consulta poderia retornar linhas diferentes quando executado duas vezes na mesma transação.

Microsoft. Data. sqlite trata o IsolationLevel passado para <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> como um nível mínimo. O nível de isolamento real será promovido para leitura não confirmada ou serializável.

O código a seguir simula uma leitura suja. Observe que a cadeia de conexão deve incluir `Cache=Shared`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]
