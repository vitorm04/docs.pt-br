---
title: Erros de banco de dados
ms.date: 12/13/2019
description: Descreve como os erros e os rearos de banco de dados são tratados pela biblioteca.
ms.openlocfilehash: 9a613b6f94a89dc40e627c14f46836be77080035
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447268"
---
# <a name="database-errors"></a>Erros de banco de dados

<xref:Microsoft.Data.Sqlite.SqliteException> é gerada quando um erro do SQLite é encontrado. A mensagem é fornecida pelo SQLite. As propriedades `SqliteErrorCode` e `SqliteExtendedErrorCode` contêm o [código de resultado](https://www.sqlite.org/rescode.html) do SQLite do erro.

Erros podem ser encontrados sempre que o Microsoft. Data. sqlite interage com a biblioteca SQLite nativa. A lista a seguir mostra os cenários comuns em que podem ocorrer erros:

* Abrindo uma conexão.
* Iniciando uma transação.
* Execução de um comando.
* Chamando <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.

Considere atentamente como seu aplicativo tratará esses erros.

## <a name="locking-retries-and-timeouts"></a>Bloqueio, novas tentativas e tempos limite

O SQLite é agressivo quando se trata de bloquear tabelas e arquivos de banco de dados. Se seu aplicativo habilitar qualquer acesso simultâneo ao banco de dados, você provavelmente encontrará erros ocupados e bloqueados. Você pode atenuar muitos erros usando um [cache compartilhado](connection-strings.md#cache) e um [log write-ahead](async.md).

Sempre que o Microsoft. Data. sqlite encontrar um erro ocupado ou bloqueado, ele será automaticamente repetido até ter sucesso ou o tempo limite do comando for atingido.

Você pode aumentar o tempo limite do comando definindo <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>. O tempo limite padrão é de 30 segundos. Um valor de `0` significa sem tempo limite.

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

O Microsoft. Data. sqlite às vezes precisa criar um objeto de comando implícito. Por exemplo, durante BeginTransaction. Para definir o tempo limite para esses comandos, use <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a>Veja também

* [Códigos de erro do SQLite](https://www.sqlite.org/rescode.html)
* [Bloqueio de arquivo no SQLite](https://www.sqlite.org/lockingv3.html)
* [Modo de cache compartilhado](https://www.sqlite.org/sharedcache.html)
* [Log write-ahead](https://www.sqlite.org/wal.html)
