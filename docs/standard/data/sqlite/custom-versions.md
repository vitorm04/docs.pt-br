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
# <a name="custom-sqlite-versions"></a><span data-ttu-id="934bd-103">Versões personalizadas do SQLite</span><span class="sxs-lookup"><span data-stu-id="934bd-103">Custom SQLite versions</span></span>

<span data-ttu-id="934bd-104">Microsoft. Data. SQLite é criado com base em SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="934bd-104">Microsoft.Data.Sqlite is built on top of SQLitePCLRaw.</span></span> <span data-ttu-id="934bd-105">Você pode usar versões personalizadas da biblioteca SQLite nativa usando um pacote ou configurando um provedor SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="934bd-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a SQLitePCLRaw provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="934bd-106">Pacotes</span><span class="sxs-lookup"><span data-stu-id="934bd-106">Bundles</span></span>

<span data-ttu-id="934bd-107">O SQLitePCLRaw fornece pacotes de pacote que facilitam a disponibilização das dependências certas em diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="934bd-107">SQLitePCLRaw provides bundle packages that make it easy to bring in the right dependencies across different platforms.</span></span>

<span data-ttu-id="934bd-108">O pacote principal Microsoft. Data. sqlite traz SQLitePCLRaw. bundle_e_sqlite3 por padrão.</span><span class="sxs-lookup"><span data-stu-id="934bd-108">The main Microsoft.Data.Sqlite package brings in SQLitePCLRaw.bundle_e_sqlite3 by default.</span></span>

<span data-ttu-id="934bd-109">Para usar um pacote diferente, instale o pacote de `Microsoft.Data.Sqlite.Core`, juntamente com o pacote de pacotes que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="934bd-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="934bd-110">Os grupos são inicializados automaticamente pelo Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="934bd-110">Bundles are automatically initialized by Microsoft.Data.Sqlite.</span></span>

| <span data-ttu-id="934bd-111">Pacote</span><span class="sxs-lookup"><span data-stu-id="934bd-111">Bundle</span></span> | <span data-ttu-id="934bd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="934bd-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="934bd-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="934bd-113">SQLitePCLRaw.bundle_e_sqlite3</span></span> | <span data-ttu-id="934bd-114">Fornece uma versão consistente do SQLite em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="934bd-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="934bd-115">Inclui FTS4, FTS5, JSON1 e</span><span class="sxs-lookup"><span data-stu-id="934bd-115">Includes the FTS4, FTS5, JSON1, and</span></span> | <span data-ttu-id="934bd-116">R \* extensões de árvore.</span><span class="sxs-lookup"><span data-stu-id="934bd-116">R\*Tree extensions.</span></span> <span data-ttu-id="934bd-117">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="934bd-117">This is the default.</span></span> |
| <span data-ttu-id="934bd-118">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="934bd-118">SQLitePCLRaw.bundle_green</span></span> | <span data-ttu-id="934bd-119">O mesmo que bundle_e_sqlite3, exceto no iOS, em que ele usa a biblioteca SQLite do sistema.</span><span class="sxs-lookup"><span data-stu-id="934bd-119">Same as bundle_e_sqlite3, except on iOS where it uses the system SQLite library.</span></span> |
| <span data-ttu-id="934bd-120">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="934bd-120">SQLitePCLRaw.bundle_zetetic</span></span> | <span data-ttu-id="934bd-121">Usa as compilações oficiais do sqlcipher de Zetetic (não incluído).</span><span class="sxs-lookup"><span data-stu-id="934bd-121">Uses the official SQLCipher builds from Zetetic (not included).</span></span> |
| <span data-ttu-id="934bd-122">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="934bd-122">SQLitePCLRaw.bundle_winsqlite3</span></span> | <span data-ttu-id="934bd-123">Usa winsqlite3. dll, a biblioteca SQLite do sistema no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="934bd-123">Uses winsqlite3.dll, the system SQLite library on Windows 10.</span></span> |
| <span data-ttu-id="934bd-124">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="934bd-124">SQLitePCLRaw.bundle_e_sqlcipher</span></span> | <span data-ttu-id="934bd-125">Fornece uma compilação de código aberto não oficial de sqlcipher.</span><span class="sxs-lookup"><span data-stu-id="934bd-125">Provides an unofficial, open-source build of SQLCipher.</span></span> |

<span data-ttu-id="934bd-126">Por exemplo, para usar a compilação de código aberto não oficial de sqlcipher, use os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="934bd-126">For example, to use the unofficial, open-source build of SQLCipher use the following commands.</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="934bd-127">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="934bd-127">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="934bd-128">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="934bd-128">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a><span data-ttu-id="934bd-129">Provedores de SQLitePCLRaw</span><span class="sxs-lookup"><span data-stu-id="934bd-129">SQLitePCLRaw providers</span></span>

<span data-ttu-id="934bd-130">Você pode usar sua própria compilação do SQLite aproveitando o pacote `SQLitePCLRaw.provider.dynamic_cdecl`.</span><span class="sxs-lookup"><span data-stu-id="934bd-130">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="934bd-131">Nesse caso, você é responsável por implantar a biblioteca nativa com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="934bd-131">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="934bd-132">Observe que os detalhes da implantação de bibliotecas nativas com seu aplicativo variam consideravelmente dependendo da plataforma .NET e do tempo de execução que você está usando.</span><span class="sxs-lookup"><span data-stu-id="934bd-132">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="934bd-133">Primeiro, você precisará implementar IGetFunctionPointer.</span><span class="sxs-lookup"><span data-stu-id="934bd-133">First, you'll need to implement IGetFunctionPointer.</span></span> <span data-ttu-id="934bd-134">A implementação é bem trivial no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="934bd-134">The implementation is fairly trivial on .NET Core.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="934bd-135">Em seguida, configure o provedor SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="934bd-135">Next, configure the SQLitePCLRaw provider.</span></span> <span data-ttu-id="934bd-136">Certifique-se de que isso é feito antes de o Microsoft. Data. sqlite ser usado em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="934bd-136">Ensure this is done before Microsoft.Data.Sqlite is used in your app.</span></span> <span data-ttu-id="934bd-137">Além disso, evite usar um pacote de pacotes SQLitePCLRaw que pode substituir seu provedor.</span><span class="sxs-lookup"><span data-stu-id="934bd-137">Also, avoid using a SQLitePCLRaw bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
