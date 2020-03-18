---
title: Cadeias de conexão
ms.date: 12/13/2019
description: As palavras-chave suportadas e os valores das strings de conexão.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400445"
---
# <a name="connection-strings"></a>Cadeias de conexão

Uma seqüência de conexões é usada para especificar como se conectar ao banco de dados. As strings de conexão no Microsoft.Data.Sqlite seguem a [sintaxe padrão ADO.NET](../../../framework/data/adonet/connection-strings.md) como uma lista de palavras-chave e valores separados por ponto e vírgula.

## <a name="keywords"></a>Palavras-chave

As seguintes palavras-chave de seqüência de conexão podem ser usadas com microsoft.data.sqlite:

### <a name="data-source"></a>Fonte de dados

O caminho do arquivo de banco de dados. *DataSource* (sem espaço) e *Filename* são aliases desta palavra-chave.

O SQLite trata caminhos relativos ao diretório de trabalho atual. Caminhos absolutos também podem ser especificados.

Se **estiver vazio,** o SQLite criará um banco de dados temporário em disco que é excluído quando a conexão é fechada.

Se `:memory:`, um banco de dados na memória é usado. Para obter mais informações, consulte [bancos de dados na memória](in-memory-databases.md).

Os caminhos `|DataDirectory|` que começam com a seqüência de substituição são tratados da mesma forma que caminhos relativos. Se definido, os caminhos serão feitos em relação ao valor de propriedade de domínio do aplicativo DataDirectory.

Esta palavra-chave também suporta [nomes de arquivos URI](https://www.sqlite.org/uri.html).

### <a name="mode"></a>Mode

O modo de conexão.

| Valor           | Descrição                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | Abre o banco de dados para leitura e escrita, e o cria se não existir. Esse é o padrão. |
| ReadWrite       | Abre o banco de dados para leitura e escrita.                                                        |
| ReadOnly        | Abre o banco de dados no modo somente leitura.                                                              |
| Memória          | Abre um banco de dados na memória.                                                                       |

### <a name="cache"></a>Cache

O modo de cache usado pela conexão.

| Valor   | Descrição                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Padrão | Usa o modo padrão da biblioteca SQLite subjacente. Esse é o padrão.                   |
| Privado | Cada conexão usa um cache privado.                                                          |
| Compartilhado  | As conexões compartilham um cache. Este modo pode alterar o comportamento da transação e do bloqueio de tabela. |

### <a name="password"></a>Senha

A chave de criptografia. Quando especificado, `PRAGMA key` é enviado imediatamente após a abertura da conexão.

> [!WARNING]
> A senha não tem efeito quando a criptografia não é suportada pela biblioteca SQLite nativa.

### <a name="foreign-keys"></a>Chaves estrangeiras

Um valor que indica se habilitaasrestrições de chave estrangeiras.

| Valor   | Descrição
| ------- | --- |
| True    | Envia `PRAGMA foreign_keys = 1` imediatamente após a abertura da conexão.
| Falso   | Envia `PRAGMA foreign_keys = 0` imediatamente após a abertura da conexão.
| (vazio) | Não envia. `PRAGMA foreign_keys` Esse é o padrão. |

Não há necessidade de habilitar chaves estrangeiras se, como em e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS foi usado para compilar a biblioteca Nativa SQLite.

### <a name="recursive-triggers"></a>Gatilhos recursivos

Um valor que indica se habilitar gatilhos recursivos.

| Valor | Descrição                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Envia `PRAGMA recursive_triggers` imediatamente após a abertura da conexão. |
| Falso | Não envia. `PRAGMA recursive_triggers` Esse é o padrão.              |

## <a name="connection-string-builder"></a>Construtor de cordas de conexão

Você pode <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> usar como uma maneira fortemente digitada de criar strings de conexão. Também pode ser usado para evitar ataques de injeção de corda de conexão.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Exemplos

### <a name="basic"></a>Basic

Uma seqüência de conexão básica com um cache compartilhado para uma concorrência melhorada.

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

### <a name="sharable-in-memory"></a>Sharable na memória

Um banco de dados sharable, na memória identificado pelo nome *Sharable.*

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Confira também

* [Cadeias de caracteres de conexão no ADO.NET](../../../framework/data/adonet/connection-strings.md)
* [Bancos de dados na memória](in-memory-databases.md)
* [Transações](transactions.md)
