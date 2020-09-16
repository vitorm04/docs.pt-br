---
title: Cadeias de conexão
ms.date: 12/13/2019
description: As palavras-chave e os valores com suporte das cadeias de conexão.
ms.openlocfilehash: 3c50b31689abf6d47aa8f83a6f6f755bcfec0ea3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555387"
---
# <a name="connection-strings"></a><span data-ttu-id="436f1-103">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="436f1-103">Connection strings</span></span>

<span data-ttu-id="436f1-104">Uma cadeia de conexão é usada para especificar como se conectar ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="436f1-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="436f1-105">As cadeias de conexão em Microsoft. Data. sqlite seguem a [sintaxe ADO.net](../../../framework/data/adonet/connection-strings.md) padrão como uma lista de palavras-chave e valores separados por ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="436f1-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="436f1-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="436f1-106">Keywords</span></span>

<span data-ttu-id="436f1-107">As palavras-chave da cadeia de conexão a seguir podem ser usadas com Microsoft. Data. sqlite:</span><span class="sxs-lookup"><span data-stu-id="436f1-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="436f1-108">Fonte de dados</span><span class="sxs-lookup"><span data-stu-id="436f1-108">Data source</span></span>

<span data-ttu-id="436f1-109">O caminho do arquivo de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="436f1-109">The path to the database file.</span></span> <span data-ttu-id="436f1-110">*DataSource* (sem espaço) e *nome de arquivo* são aliases dessa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="436f1-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="436f1-111">O SQLite trata caminhos relativos ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="436f1-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="436f1-112">Caminhos absolutos também podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="436f1-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="436f1-113">Se **estiver vazio**, o SQLite criará um banco de dados temporário em disco que é excluído quando a conexão é fechada.</span><span class="sxs-lookup"><span data-stu-id="436f1-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="436f1-114">Se `:memory:` , um banco de dados na memória é usado.</span><span class="sxs-lookup"><span data-stu-id="436f1-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="436f1-115">Para obter mais informações, consulte [bancos de dados na memória](in-memory-databases.md).</span><span class="sxs-lookup"><span data-stu-id="436f1-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="436f1-116">Os caminhos que começam com a `|DataDirectory|` cadeia de caracteres de substituição são tratados da mesma forma que os caminhos relativos.</span><span class="sxs-lookup"><span data-stu-id="436f1-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="436f1-117">Se definido, os caminhos são feitos em relação ao valor da propriedade de domínio do aplicativo DataDirectory.</span><span class="sxs-lookup"><span data-stu-id="436f1-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="436f1-118">Essa palavra-chave também dá suporte a [nomes de fileuri](https://www.sqlite.org/uri.html).</span><span class="sxs-lookup"><span data-stu-id="436f1-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="436f1-119">Modo</span><span class="sxs-lookup"><span data-stu-id="436f1-119">Mode</span></span>

<span data-ttu-id="436f1-120">O modo de conexão.</span><span class="sxs-lookup"><span data-stu-id="436f1-120">The connection mode.</span></span>

| <span data-ttu-id="436f1-121">Valor</span><span class="sxs-lookup"><span data-stu-id="436f1-121">Value</span></span>           | <span data-ttu-id="436f1-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="436f1-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="436f1-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="436f1-123">ReadWriteCreate</span></span> | <span data-ttu-id="436f1-124">Abre o banco de dados para leitura e gravação e cria-o se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="436f1-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="436f1-125">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="436f1-125">This is the default.</span></span> |
| <span data-ttu-id="436f1-126">ReadWrite</span><span class="sxs-lookup"><span data-stu-id="436f1-126">ReadWrite</span></span>       | <span data-ttu-id="436f1-127">Abre o banco de dados para leitura e gravação.</span><span class="sxs-lookup"><span data-stu-id="436f1-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="436f1-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="436f1-128">ReadOnly</span></span>        | <span data-ttu-id="436f1-129">Abre o banco de dados no modo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="436f1-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="436f1-130">Memória</span><span class="sxs-lookup"><span data-stu-id="436f1-130">Memory</span></span>          | <span data-ttu-id="436f1-131">Abre um banco de dados na memória.</span><span class="sxs-lookup"><span data-stu-id="436f1-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="436f1-132">Cache</span><span class="sxs-lookup"><span data-stu-id="436f1-132">Cache</span></span>

<span data-ttu-id="436f1-133">O modo de cache usado pela conexão.</span><span class="sxs-lookup"><span data-stu-id="436f1-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="436f1-134">Valor</span><span class="sxs-lookup"><span data-stu-id="436f1-134">Value</span></span>   | <span data-ttu-id="436f1-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="436f1-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="436f1-136">Padrão</span><span class="sxs-lookup"><span data-stu-id="436f1-136">Default</span></span> | <span data-ttu-id="436f1-137">Usa o modo padrão da biblioteca SQLite subjacente.</span><span class="sxs-lookup"><span data-stu-id="436f1-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="436f1-138">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="436f1-138">This is the default.</span></span>                   |
| <span data-ttu-id="436f1-139">Particular</span><span class="sxs-lookup"><span data-stu-id="436f1-139">Private</span></span> | <span data-ttu-id="436f1-140">Cada conexão usa um cache privado.</span><span class="sxs-lookup"><span data-stu-id="436f1-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="436f1-141">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="436f1-141">Shared</span></span>  | <span data-ttu-id="436f1-142">As conexões compartilham um cache.</span><span class="sxs-lookup"><span data-stu-id="436f1-142">Connections share a cache.</span></span> <span data-ttu-id="436f1-143">Esse modo pode alterar o comportamento do bloqueio de transação e tabela.</span><span class="sxs-lookup"><span data-stu-id="436f1-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="436f1-144">Senha</span><span class="sxs-lookup"><span data-stu-id="436f1-144">Password</span></span>

<span data-ttu-id="436f1-145">A chave de criptografia.</span><span class="sxs-lookup"><span data-stu-id="436f1-145">The encryption key.</span></span> <span data-ttu-id="436f1-146">Quando especificado, `PRAGMA key` é enviado imediatamente após a abertura da conexão.</span><span class="sxs-lookup"><span data-stu-id="436f1-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="436f1-147">A senha não tem efeito quando a criptografia não tem suporte da biblioteca SQLite nativa.</span><span class="sxs-lookup"><span data-stu-id="436f1-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="436f1-148">Chaves estrangeiras</span><span class="sxs-lookup"><span data-stu-id="436f1-148">Foreign Keys</span></span>

<span data-ttu-id="436f1-149">Um valor que indica se as restrições de chave estrangeira devem ser habilitadas.</span><span class="sxs-lookup"><span data-stu-id="436f1-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="436f1-150">Valor</span><span class="sxs-lookup"><span data-stu-id="436f1-150">Value</span></span>   | <span data-ttu-id="436f1-151">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="436f1-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="436f1-152">True</span><span class="sxs-lookup"><span data-stu-id="436f1-152">True</span></span>    | <span data-ttu-id="436f1-153">Envia `PRAGMA foreign_keys = 1` imediatamente após a abertura da conexão.</span><span class="sxs-lookup"><span data-stu-id="436f1-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="436f1-154">Falso</span><span class="sxs-lookup"><span data-stu-id="436f1-154">False</span></span>   | <span data-ttu-id="436f1-155">Envia `PRAGMA foreign_keys = 0` imediatamente após a abertura da conexão.</span><span class="sxs-lookup"><span data-stu-id="436f1-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="436f1-156">(vazio)</span><span class="sxs-lookup"><span data-stu-id="436f1-156">(empty)</span></span> | <span data-ttu-id="436f1-157">Não envia `PRAGMA foreign_keys` .</span><span class="sxs-lookup"><span data-stu-id="436f1-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="436f1-158">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="436f1-158">This is the default.</span></span> |

<span data-ttu-id="436f1-159">Não há necessidade de habilitar chaves estrangeiras se, como em e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS foi usado para compilar a biblioteca SQLite nativa.</span><span class="sxs-lookup"><span data-stu-id="436f1-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="436f1-160">Gatilhos recursivos</span><span class="sxs-lookup"><span data-stu-id="436f1-160">Recursive triggers</span></span>

<span data-ttu-id="436f1-161">Um valor que indica se os gatilhos recursivos devem ser habilitados.</span><span class="sxs-lookup"><span data-stu-id="436f1-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="436f1-162">Valor</span><span class="sxs-lookup"><span data-stu-id="436f1-162">Value</span></span> | <span data-ttu-id="436f1-163">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="436f1-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="436f1-164">True</span><span class="sxs-lookup"><span data-stu-id="436f1-164">True</span></span>  | <span data-ttu-id="436f1-165">Envia `PRAGMA recursive_triggers` imediatamente após a abertura da conexão.</span><span class="sxs-lookup"><span data-stu-id="436f1-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="436f1-166">Falso</span><span class="sxs-lookup"><span data-stu-id="436f1-166">False</span></span> | <span data-ttu-id="436f1-167">Não envia `PRAGMA recursive_triggers` .</span><span class="sxs-lookup"><span data-stu-id="436f1-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="436f1-168">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="436f1-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="436f1-169">Construtor de cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="436f1-169">Connection string builder</span></span>

<span data-ttu-id="436f1-170">Você pode usar <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> como uma maneira fortemente tipada de criar cadeias de conexão.</span><span class="sxs-lookup"><span data-stu-id="436f1-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="436f1-171">Ele também pode ser usado para evitar ataques de injeção de cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="436f1-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="436f1-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="436f1-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="436f1-173">Basic</span><span class="sxs-lookup"><span data-stu-id="436f1-173">Basic</span></span>

<span data-ttu-id="436f1-174">Uma cadeia de conexão básica com um cache compartilhado para simultaneidade aprimorada.</span><span class="sxs-lookup"><span data-stu-id="436f1-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```connectionstring
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="436f1-175">Criptografado</span><span class="sxs-lookup"><span data-stu-id="436f1-175">Encrypted</span></span>

<span data-ttu-id="436f1-176">Um banco de dados criptografado.</span><span class="sxs-lookup"><span data-stu-id="436f1-176">An encrypted database.</span></span>

```connectionstring
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="436f1-177">Somente leitura</span><span class="sxs-lookup"><span data-stu-id="436f1-177">Read-only</span></span>

<span data-ttu-id="436f1-178">Um banco de dados somente leitura que não pode ser modificado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="436f1-178">A read-only database that cannot be modified by the app.</span></span>

```connectionstring
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="436f1-179">Na memória</span><span class="sxs-lookup"><span data-stu-id="436f1-179">In-memory</span></span>

<span data-ttu-id="436f1-180">Um banco de dados privado na memória.</span><span class="sxs-lookup"><span data-stu-id="436f1-180">A private, in-memory database.</span></span>

```connectionstring
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="436f1-181">Compartilhável na memória</span><span class="sxs-lookup"><span data-stu-id="436f1-181">Sharable in-memory</span></span>

<span data-ttu-id="436f1-182">Um banco de dados compartilhável e na memória identificado pelo nome *compartilhável*.</span><span class="sxs-lookup"><span data-stu-id="436f1-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```connectionstring
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="436f1-183">Confira também</span><span class="sxs-lookup"><span data-stu-id="436f1-183">See also</span></span>

* [<span data-ttu-id="436f1-184">Cadeias de caracteres de conexão no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="436f1-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="436f1-185">Bancos de dados na memória</span><span class="sxs-lookup"><span data-stu-id="436f1-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="436f1-186">Transações</span><span class="sxs-lookup"><span data-stu-id="436f1-186">Transactions</span></span>](transactions.md)
