---
title: Criptografia
ms.date: 09/08/2020
description: Saiba como criptografar seu arquivo de banco de dados.
ms.openlocfilehash: 1b33e1510a269aba87caba2cd39faab33791aa55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203404"
---
# <a name="encryption"></a><span data-ttu-id="cb3af-103">Criptografia</span><span class="sxs-lookup"><span data-stu-id="cb3af-103">Encryption</span></span>

<span data-ttu-id="cb3af-104">O SQLite não dá suporte a criptografia de arquivos de banco de dados por padrão.</span><span class="sxs-lookup"><span data-stu-id="cb3af-104">SQLite doesn't support encrypting database files by default.</span></span> <span data-ttu-id="cb3af-105">Em vez disso, você precisa usar uma versão modificada do SQLite, como [Ver](https://www.hwaci.com/sw/sqlite/see.html), [sqlcipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/)ou [wxSQLite3](https://utelle.github.io/wxsqlite3).</span><span class="sxs-lookup"><span data-stu-id="cb3af-105">Instead, you need to use a modified version of SQLite like [SEE](https://www.hwaci.com/sw/sqlite/see.html), [SQLCipher](https://www.zetetic.net/sqlcipher/), [SQLiteCrypt](http://www.sqlite-crypt.com/), or [wxSQLite3](https://utelle.github.io/wxsqlite3).</span></span> <span data-ttu-id="cb3af-106">Este artigo demonstra o uso de uma compilação sem suporte de código-fonte aberto de sqlcipher, mas as informações também se aplicam a outras soluções, pois geralmente seguem o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="cb3af-106">This article demonstrates using an unsupported, open-source build of SQLCipher, but the information also applies to other solutions since they generally follow the same pattern.</span></span>

## <a name="installation"></a><span data-ttu-id="cb3af-107">Instalação</span><span class="sxs-lookup"><span data-stu-id="cb3af-107">Installation</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="cb3af-108">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cb3af-108">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet remove package Microsoft.Data.Sqlite
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="cb3af-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb3af-109">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Remove-Package Microsoft.Data.Sqlite
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

<span data-ttu-id="cb3af-110">Para obter mais informações sobre como usar uma biblioteca nativa diferente para criptografia, consulte [versões personalizadas do SQLite](custom-versions.md).</span><span class="sxs-lookup"><span data-stu-id="cb3af-110">For more information about using a different native library for encryption, see [Custom SQLite versions](custom-versions.md).</span></span>

## <a name="specify-the-key"></a><span data-ttu-id="cb3af-111">Especifique a chave</span><span class="sxs-lookup"><span data-stu-id="cb3af-111">Specify the key</span></span>

<span data-ttu-id="cb3af-112">Para habilitar a criptografia em um novo banco de dados, especifique a chave usando a `Password` palavra-chave da cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="cb3af-112">To enable encryption on a new database, specify the key using the `Password` connection string keyword.</span></span> <span data-ttu-id="cb3af-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> para adicionar ou atualizar o valor da entrada do usuário e evitar ataques de injeção de cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="cb3af-113">Use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> to add or update the value from user input and avoid connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

> [!TIP]
> <span data-ttu-id="cb3af-114">O método para criptografar e descriptografar bancos de dados existentes varia de acordo com a solução que você está usando.</span><span class="sxs-lookup"><span data-stu-id="cb3af-114">The method for encrypting and decrypting existing databases varies depending on which solution you're using.</span></span> <span data-ttu-id="cb3af-115">Por exemplo, você precisa usar a `sqlcipher_export()` função em sqlcipher.</span><span class="sxs-lookup"><span data-stu-id="cb3af-115">For example, you need to use the `sqlcipher_export()` function on SQLCipher.</span></span> <span data-ttu-id="cb3af-116">Verifique a documentação da solução para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="cb3af-116">Check your solution's documentation for details.</span></span>

## <a name="rekeying-the-database"></a><span data-ttu-id="cb3af-117">Rechaveamento do banco de dados</span><span class="sxs-lookup"><span data-stu-id="cb3af-117">Rekeying the database</span></span>

<span data-ttu-id="cb3af-118">Se você quiser alterar a chave de um banco de dados criptografado, emita uma `PRAGMA rekey` instrução.</span><span class="sxs-lookup"><span data-stu-id="cb3af-118">If you want to change the key of an encrypted database, issue a `PRAGMA rekey` statement.</span></span>

<span data-ttu-id="cb3af-119">Infelizmente, o SQLite não dá suporte a parâmetros em `PRAGMA` instruções.</span><span class="sxs-lookup"><span data-stu-id="cb3af-119">Unfortunately, SQLite doesn't support parameters in `PRAGMA` statements.</span></span> <span data-ttu-id="cb3af-120">Em vez disso, use a `quote()` função para impedir a injeção de SQL.</span><span class="sxs-lookup"><span data-stu-id="cb3af-120">Instead, use the `quote()` function to prevent SQL injection.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_Rekey)]
