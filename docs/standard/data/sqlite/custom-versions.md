---
title: Versões personalizadas do SQLite
ms.date: 12/13/2019
description: Saiba como usar uma versão personalizada da biblioteca SQLite nativa.
ms.openlocfilehash: 8a2646138ea9dbecf412a2e8e0e347e2d71a5b0b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447142"
---
# <a name="custom-sqlite-versions"></a>Versões personalizadas do SQLite

Microsoft. Data. SQLite é criado com base em SQLitePCLRaw. Você pode usar versões personalizadas da biblioteca SQLite nativa usando um pacote ou configurando um provedor SQLitePCLRaw.

## <a name="bundles"></a>Pacotes

O SQLitePCLRaw fornece pacotes de pacote que facilitam a disponibilização das dependências certas em diferentes plataformas.

O pacote principal Microsoft. Data. sqlite traz SQLitePCLRaw. bundle_e_sqlite3 por padrão.

Para usar um pacote diferente, instale o pacote de `Microsoft.Data.Sqlite.Core`, juntamente com o pacote de pacotes que você deseja usar. Os grupos são inicializados automaticamente pelo Microsoft. Data. sqlite.

| Pacote | Descrição |
| --- | --- |
| SQLitePCLRaw. bundle_e_sqlite3 | Fornece uma versão consistente do SQLite em todas as plataformas. Inclui FTS4, FTS5, JSON1 e | R * extensões de árvore. Este é o padrão. |
| SQLitePCLRaw. bundle_green | O mesmo que bundle_e_sqlite3, exceto no iOS, em que ele usa a biblioteca SQLite do sistema. |
| SQLitePCLRaw. bundle_zetetic | Usa as compilações oficiais do sqlcipher de Zetetic (não incluído). |
| SQLitePCLRaw. bundle_winsqlite3 | Usa winsqlite3. dll, a biblioteca SQLite do sistema no Windows 10. |
| SQLitePCLRaw. bundle_e_sqlcipher | Fornece uma compilação de código aberto não oficial de sqlcipher. |

Por exemplo, para usar a compilação de código aberto não oficial de sqlcipher, use os comandos a seguir.

### <a name="net-core-clitabnetcore-cli"></a>[CLI do .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a>Provedores de SQLitePCLRaw

Você pode usar sua própria compilação do SQLite aproveitando o pacote `SQLitePCLRaw.provider.dynamic_cdecl`. Nesse caso, você é responsável por implantar a biblioteca nativa com seu aplicativo. Observe que os detalhes da implantação de bibliotecas nativas com seu aplicativo variam consideravelmente dependendo da plataforma .NET e do tempo de execução que você está usando.

Primeiro, você precisará implementar IGetFunctionPointer. A implementação é bem trivial no .NET Core.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

Em seguida, configure o provedor SQLitePCLRaw. Certifique-se de que isso é feito antes de o Microsoft. Data. sqlite ser usado em seu aplicativo. Além disso, evite usar um pacote de pacotes SQLitePCLRaw que pode substituir seu provedor.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
