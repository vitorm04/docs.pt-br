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
# <a name="encryption"></a><span data-ttu-id="faf9e-103">Criptografia</span><span class="sxs-lookup"><span data-stu-id="faf9e-103">Encryption</span></span>

<span data-ttu-id="faf9e-104">O SQLite não dá suporte a criptografia de arquivos de banco de dados por padrão.</span><span class="sxs-lookup"><span data-stu-id="faf9e-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="faf9e-105">Em vez disso, você precisa usar uma versão modificada do SQLite, como [Ver](https://www.hwaci.com/sw/sqlite/see.html), [sqlcipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)ou [wxSQLite3](https://utelle.github.io/wxsqlite3).</span><span class="sxs-lookup"><span data-stu-id="faf9e-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="faf9e-106">Este artigo demonstra o uso de uma compilação sem suporte de código-fonte aberto de sqlcipher, mas as informações também se aplicam a outras soluções, pois geralmente seguem o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="faf9e-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="faf9e-107">Instalação</span><span class="sxs-lookup"><span data-stu-id="faf9e-107">Installation</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="faf9e-108">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="faf9e-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="faf9e-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="faf9e-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="faf9e-110">Para obter mais informações sobre como usar uma biblioteca nativa diferente para criptografia, consulte [versões personalizadas do SQLite](custom-versions.md).</span><span class="sxs-lookup"><span data-stu-id="faf9e-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="faf9e-111">Especifique a chave</span><span class="sxs-lookup"><span data-stu-id="faf9e-111">Specify the key</span></span>

<span data-ttu-id="faf9e-112">Para habilitar a criptografia, especifique a chave usando a palavra-chave da cadeia de conexão `Password`.</span><span class="sxs-lookup"><span data-stu-id="faf9e-112">To enable encryption, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="faf9e-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> para adicionar ou atualizar o valor da entrada do usuário e evitar ataques de injeção de cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="faf9e-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="rekeying-the-database"></a><span data-ttu-id="faf9e-114">Rechaveamento do banco de dados</span><span class="sxs-lookup"><span data-stu-id="faf9e-114">Rekeying the database</span></span>

<span data-ttu-id="faf9e-115">Se você quiser alterar a chave de criptografia de um banco de dados, emita uma instrução `PRAGMA rekey`.</span><span class="sxs-lookup"><span data-stu-id="faf9e-115">If you want to change the encryption key of a database, issue a `PRAGMA rekey` statement.</span></span> <span data-ttu-id="faf9e-116">Para descriptografar o banco de dados, especifique `NULL`.</span><span class="sxs-lookup"><span data-stu-id="faf9e-116">To decrypt the database, specify `NULL`.</span></span>

<span data-ttu-id="faf9e-117">Infelizmente, o SQLite não dá suporte a parâmetros em instruções `PRAGMA`.</span><span class="sxs-lookup"><span data-stu-id="faf9e-117">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="faf9e-118">Em vez disso, use a função `quote()` para impedir a injeção de SQL.</span><span class="sxs-lookup"><span data-stu-id="faf9e-118">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
