---
title: Cadeias de conexão
ms.date: 12/13/2019
description: As palavras-chave e os valores com suporte das cadeias de conexão.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400445"
---
# <a name="connection-strings"></a>Cadeias de conexão

Uma cadeia de conexão é usada para especificar como se conectar ao banco de dados. As cadeias de conexão em Microsoft. Data. sqlite seguem a [sintaxe ADO.net](../../../framework/data/adonet/connection-strings.md) padrão como uma lista de palavras-chave e valores separados por ponto e vírgula.

## <a name="keywords"></a>Palavras-chave

As palavras-chave da cadeia de conexão a seguir podem ser usadas com Microsoft. Data. sqlite:

### <a name="data-source"></a>Fonte de dados

O caminho do arquivo de banco de dados. *DataSource* (sem espaço) e *nome de arquivo* são aliases dessa palavra-chave.

O SQLite trata caminhos relativos ao diretório de trabalho atual. Caminhos absolutos também podem ser especificados.

Se **estiver vazio**, o SQLite criará um banco de dados temporário em disco que é excluído quando a conexão é fechada.

Se `:memory:`, um banco de dados na memória é usado. Para obter mais informações, consulte [bancos de dados na memória](in-memory-databases.md).

Os caminhos que começam com `|DataDirectory|` a cadeia de caracteres de substituição são tratados da mesma forma que os caminhos relativos. Se definido, os caminhos são feitos em relação ao valor da propriedade de domínio do aplicativo DataDirectory.

Essa palavra-chave também dá suporte a [nomes de fileuri](https://www.sqlite.org/uri.html).

### <a name="mode"></a>Mode

O modo de conexão.

| Valor           | Descrição                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | Abre o banco de dados para leitura e gravação e cria-o se ele não existir. Esse é o padrão. |
| ReadWrite       | Abre o banco de dados para leitura e gravação.                                                        |
| ReadOnly        | Abre o banco de dados no modo somente leitura.                                                              |
| Memória          | Abre um banco de dados na memória.                                                                       |

### <a name="cache"></a>Cache

O modo de cache usado pela conexão.

| Valor   | Descrição                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Padrão | Usa o modo padrão da biblioteca SQLite subjacente. Esse é o padrão.                   |
| Privado | Cada conexão usa um cache privado.                                                          |
| Compartilhado  | As conexões compartilham um cache. Esse modo pode alterar o comportamento do bloqueio de transação e tabela. |

### <a name="password"></a>Senha

A chave de criptografia. Quando especificado, `PRAGMA key` é enviado imediatamente após a abertura da conexão.

> [!WARNING]
> A senha não tem efeito quando a criptografia não tem suporte da biblioteca SQLite nativa.

### <a name="foreign-keys"></a>Chaves estrangeiras

Um valor que indica se as restrições de chave estrangeira devem ser habilitadas.

| Valor   | Descrição
| ------- | --- |
| True    | Envia `PRAGMA foreign_keys = 1` imediatamente após a abertura da conexão.
| Falso   | Envia `PRAGMA foreign_keys = 0` imediatamente após a abertura da conexão.
| (vazio) | Não envia `PRAGMA foreign_keys`. Esse é o padrão. |

Não há necessidade de habilitar chaves estrangeiras se, como em e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS foi usado para compilar a biblioteca SQLite nativa.

### <a name="recursive-triggers"></a>Gatilhos recursivos

Um valor que indica se os gatilhos recursivos devem ser habilitados.

| Valor | Descrição                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Envia `PRAGMA recursive_triggers` imediatamente após a abertura da conexão. |
| Falso | Não envia `PRAGMA recursive_triggers`. Esse é o padrão.              |

## <a name="connection-string-builder"></a>Construtor de cadeia de conexão

Você pode usar <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> como uma maneira fortemente tipada de criar cadeias de conexão. Ele também pode ser usado para evitar ataques de injeção de cadeia de conexão.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Exemplos

### <a name="basic"></a>Basic

Uma cadeia de conexão básica com um cache compartilhado para simultaneidade aprimorada.

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Criptografado

Um banco de dados criptografado.

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>Somente leitura

Um banco de dados somente leitura que não pode ser modificado pelo aplicativo.

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>Na memória

Um banco de dados privado na memória.

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>Compartilhável na memória

Um banco de dados compartilhável e na memória identificado pelo nome *compartilhável*.

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Veja também

* [Cadeias de caracteres de conexão no ADO.NET](../../../framework/data/adonet/connection-strings.md)
* [Bancos de dados na memória](in-memory-databases.md)
* [Transactions](transactions.md)
