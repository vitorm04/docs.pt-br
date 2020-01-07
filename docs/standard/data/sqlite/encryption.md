---
title: Criptografia
ms.date: 12/13/2019
description: Saiba como criptografar seu arquivo de banco de dados.
ms.openlocfilehash: ccdd4b6b8642b3cde1c2667c9ca432a9b0ef21f2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447261"
---
# <a name="encryption"></a>Criptografia

O SQLite não dá suporte a criptografia de arquivos de banco de dados por padrão. Em vez disso, você precisa usar uma versão modificada do SQLite, como [Ver](https://www.hwaci.com/sw/sqlite/see.html), [sqlcipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)ou [wxSQLite3](https://utelle.github.io/wxsqlite3). Este artigo demonstra o uso de uma compilação sem suporte de código-fonte aberto de sqlcipher, mas as informações também se aplicam a outras soluções, pois geralmente seguem o mesmo padrão.

## <a name="installation"></a>Instalação

### <a name="net-core-clitabnetcore-cli"></a>[CLI do .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

Para obter mais informações sobre como usar uma biblioteca nativa diferente para criptografia, consulte [versões personalizadas do SQLite](custom-versions.md).

## <a name="specify-the-key"></a>Especifique a chave

Para habilitar a criptografia, especifique a chave usando a palavra-chave da cadeia de conexão `Password`. Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> para adicionar ou atualizar o valor da entrada do usuário e evitar ataques de injeção de cadeia de conexão.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a>Rechaveamento do banco de dados

Se você quiser alterar a chave de criptografia de um banco de dados, emita uma instrução `PRAGMA rekey`. Para descriptografar o banco de dados, especifique `NULL`.

Infelizmente, o SQLite não dá suporte a parâmetros em instruções `PRAGMA`. Em vez disso, use a função `quote()` para impedir a injeção de SQL.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
