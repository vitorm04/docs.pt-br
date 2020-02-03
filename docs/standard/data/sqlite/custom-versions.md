---
title: Versões personalizadas do SQLite
ms.date: 12/13/2019
description: Saiba como usar uma versão personalizada da biblioteca SQLite nativa.
ms.openlocfilehash: dd27278c1dbe17b12e5067d04d19043bf259b1e8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746985"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="e3f08-103">Versões personalizadas do SQLite</span><span class="sxs-lookup"><span data-stu-id="e3f08-103">Custom SQLite versions</span></span>

<span data-ttu-id="e3f08-104">Microsoft. Data. SQLite é criado com base em SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="e3f08-104">Microsoft.Data.Sqlite is built on top of SQLitePCLRaw.</span></span> <span data-ttu-id="e3f08-105">Você pode usar versões personalizadas da biblioteca SQLite nativa usando um pacote ou configurando um provedor SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="e3f08-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a SQLitePCLRaw provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="e3f08-106">Pacotes</span><span class="sxs-lookup"><span data-stu-id="e3f08-106">Bundles</span></span>

<span data-ttu-id="e3f08-107">O SQLitePCLRaw fornece pacotes de pacote que facilitam a disponibilização das dependências certas em diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="e3f08-107">SQLitePCLRaw provides bundle packages that make it easy to bring in the right dependencies across different platforms.</span></span>

<span data-ttu-id="e3f08-108">O pacote principal Microsoft. Data. sqlite traz SQLitePCLRaw. bundle_e_sqlite3 por padrão.</span><span class="sxs-lookup"><span data-stu-id="e3f08-108">The main Microsoft.Data.Sqlite package brings in SQLitePCLRaw.bundle_e_sqlite3 by default.</span></span>

<span data-ttu-id="e3f08-109">Para usar um pacote diferente, instale o pacote de `Microsoft.Data.Sqlite.Core`, juntamente com o pacote de pacotes que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="e3f08-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="e3f08-110">Os grupos são inicializados automaticamente pelo Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="e3f08-110">Bundles are automatically initialized by Microsoft.Data.Sqlite.</span></span>

| <span data-ttu-id="e3f08-111">Pacote</span><span class="sxs-lookup"><span data-stu-id="e3f08-111">Bundle</span></span> | <span data-ttu-id="e3f08-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3f08-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e3f08-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="e3f08-113">SQLitePCLRaw.bundle_e_sqlite3</span></span> | <span data-ttu-id="e3f08-114">Fornece uma versão consistente do SQLite em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="e3f08-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="e3f08-115">Inclui as extensões de árvore FTS4, FTS5, JSON1 e R \*.</span><span class="sxs-lookup"><span data-stu-id="e3f08-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="e3f08-116">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="e3f08-116">This is the default.</span></span> |
| <span data-ttu-id="e3f08-117">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="e3f08-117">SQLitePCLRaw.bundle_green</span></span> | <span data-ttu-id="e3f08-118">O mesmo que bundle_e_sqlite3, exceto no iOS, em que ele usa a biblioteca SQLite do sistema.</span><span class="sxs-lookup"><span data-stu-id="e3f08-118">Same as bundle_e_sqlite3, except on iOS where it uses the system SQLite library.</span></span> |
| <span data-ttu-id="e3f08-119">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="e3f08-119">SQLitePCLRaw.bundle_zetetic</span></span> | <span data-ttu-id="e3f08-120">Usa as compilações oficiais do sqlcipher de Zetetic (não incluído).</span><span class="sxs-lookup"><span data-stu-id="e3f08-120">Uses the official SQLCipher builds from Zetetic (not included).</span></span> |
| <span data-ttu-id="e3f08-121">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="e3f08-121">SQLitePCLRaw.bundle_winsqlite3</span></span> | <span data-ttu-id="e3f08-122">Usa winsqlite3. dll, a biblioteca SQLite do sistema no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e3f08-122">Uses winsqlite3.dll, the system SQLite library on Windows 10.</span></span> |
| <span data-ttu-id="e3f08-123">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="e3f08-123">SQLitePCLRaw.bundle_e_sqlcipher</span></span> | <span data-ttu-id="e3f08-124">Fornece uma compilação de código aberto não oficial de sqlcipher.</span><span class="sxs-lookup"><span data-stu-id="e3f08-124">Provides an unofficial, open-source build of SQLCipher.</span></span> |

<span data-ttu-id="e3f08-125">Por exemplo, para usar a compilação de código aberto não oficial de sqlcipher, use os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="e3f08-125">For example, to use the unofficial, open-source build of SQLCipher use the following commands.</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="e3f08-126">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e3f08-126">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="e3f08-127">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e3f08-127">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a><span data-ttu-id="e3f08-128">Provedores de SQLitePCLRaw</span><span class="sxs-lookup"><span data-stu-id="e3f08-128">SQLitePCLRaw providers</span></span>

<span data-ttu-id="e3f08-129">Você pode usar sua própria compilação do SQLite aproveitando o pacote `SQLitePCLRaw.provider.dynamic_cdecl`.</span><span class="sxs-lookup"><span data-stu-id="e3f08-129">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="e3f08-130">Nesse caso, você é responsável por implantar a biblioteca nativa com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3f08-130">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="e3f08-131">Observe que os detalhes da implantação de bibliotecas nativas com seu aplicativo variam consideravelmente dependendo da plataforma .NET e do tempo de execução que você está usando.</span><span class="sxs-lookup"><span data-stu-id="e3f08-131">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="e3f08-132">Primeiro, você precisará implementar IGetFunctionPointer.</span><span class="sxs-lookup"><span data-stu-id="e3f08-132">First, you'll need to implement IGetFunctionPointer.</span></span> <span data-ttu-id="e3f08-133">A implementação é bem trivial no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e3f08-133">The implementation is fairly trivial on .NET Core.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="e3f08-134">Em seguida, configure o provedor SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="e3f08-134">Next, configure the SQLitePCLRaw provider.</span></span> <span data-ttu-id="e3f08-135">Certifique-se de que isso é feito antes de o Microsoft. Data. sqlite ser usado em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3f08-135">Ensure this is done before Microsoft.Data.Sqlite is used in your app.</span></span> <span data-ttu-id="e3f08-136">Além disso, evite usar um pacote de pacotes SQLitePCLRaw que pode substituir seu provedor.</span><span class="sxs-lookup"><span data-stu-id="e3f08-136">Also, avoid using a SQLitePCLRaw bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
