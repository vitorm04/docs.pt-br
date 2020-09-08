---
title: Versões personalizadas do SQLite
ms.date: 09/04/2020
description: Saiba como usar uma versão personalizada da biblioteca SQLite nativa.
ms.openlocfilehash: fbf4b4cd33e6e890ce0c0cfe0b7688487b94b4a3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516132"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="606f1-103">Versões personalizadas do SQLite</span><span class="sxs-lookup"><span data-stu-id="606f1-103">Custom SQLite versions</span></span>

<span data-ttu-id="606f1-104">`Microsoft.Data.Sqlite` é criado com base em `SQLitePCLRaw` .</span><span class="sxs-lookup"><span data-stu-id="606f1-104">`Microsoft.Data.Sqlite` is built on top of `SQLitePCLRaw`.</span></span> <span data-ttu-id="606f1-105">Você pode usar versões personalizadas da biblioteca SQLite nativa usando um pacote ou configurando um `SQLitePCLRaw` provedor.</span><span class="sxs-lookup"><span data-stu-id="606f1-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a `SQLitePCLRaw` provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="606f1-106">Pacotes</span><span class="sxs-lookup"><span data-stu-id="606f1-106">Bundles</span></span>

<span data-ttu-id="606f1-107">`SQLitePCLRaw` fornece pacotes de pacote baseados em conveniência, que facilitam a tarefa de trazer as dependências certas entre diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="606f1-107">`SQLitePCLRaw` provides convenience-based bundle packages, that make it easy to bring in the right dependencies across different platforms.</span></span> <span data-ttu-id="606f1-108">O `Microsoft.Data.Sqlite` pacote principal traz `SQLitePCLRaw.bundle_e_sqlite3` por padrão.</span><span class="sxs-lookup"><span data-stu-id="606f1-108">The main `Microsoft.Data.Sqlite` package brings in `SQLitePCLRaw.bundle_e_sqlite3` by default.</span></span> <span data-ttu-id="606f1-109">Para usar um pacote diferente, instale o `Microsoft.Data.Sqlite.Core` pacote, juntamente com o pacote de pacotes que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="606f1-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="606f1-110">Os grupos são inicializados automaticamente pelo `Microsoft.Data.Sqlite` .</span><span class="sxs-lookup"><span data-stu-id="606f1-110">Bundles are automatically initialized by `Microsoft.Data.Sqlite`.</span></span>

| <span data-ttu-id="606f1-111">Pacote</span><span class="sxs-lookup"><span data-stu-id="606f1-111">Bundle</span></span> | <span data-ttu-id="606f1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="606f1-112">Description</span></span> |
|--|--|
| [<span data-ttu-id="606f1-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="606f1-113">SQLitePCLRaw.bundle_e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | <span data-ttu-id="606f1-114">Fornece uma versão consistente do SQLite em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="606f1-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="606f1-115">Inclui as extensões de árvore FTS4, FTS5, JSON1 e R \*.</span><span class="sxs-lookup"><span data-stu-id="606f1-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="606f1-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="606f1-116">This is the default.</span></span> |
| [<span data-ttu-id="606f1-117">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="606f1-117">SQLitePCLRaw.bundle_e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | <span data-ttu-id="606f1-118">Fornece uma compilação não oficial de código aberto do `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="606f1-118">Provides an unofficial, open-source build of `SQLCipher`.</span></span> |
| [<span data-ttu-id="606f1-119">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="606f1-119">SQLitePCLRaw.bundle_green</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | <span data-ttu-id="606f1-120">O mesmo que `bundle_e_sqlite3` , exceto no Ios, em que ele usa a biblioteca SQLite do sistema.</span><span class="sxs-lookup"><span data-stu-id="606f1-120">Same as `bundle_e_sqlite3`, except on iOS where it uses the system SQLite library.</span></span> |
| [<span data-ttu-id="606f1-121">SQLitePCLRaw. bundle_sqlite3</span><span class="sxs-lookup"><span data-stu-id="606f1-121">SQLitePCLRaw.bundle_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_sqlite3) | <span data-ttu-id="606f1-122">Usa a biblioteca SQLite do sistema.</span><span class="sxs-lookup"><span data-stu-id="606f1-122">Uses the system SQLite library.</span></span> |
| [<span data-ttu-id="606f1-123">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="606f1-123">SQLitePCLRaw.bundle_winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | <span data-ttu-id="606f1-124">Usa `winsqlite3.dll` o, a biblioteca SQLite do sistema no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="606f1-124">Uses `winsqlite3.dll`, the system SQLite library on Windows 10.</span></span> |
| [<span data-ttu-id="606f1-125">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="606f1-125">SQLitePCLRaw.bundle_zetetic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | <span data-ttu-id="606f1-126">Usa as `SQLCipher` compilações oficiais do Zetetic (não incluído).</span><span class="sxs-lookup"><span data-stu-id="606f1-126">Uses the official `SQLCipher` builds from Zetetic (not included).</span></span> |

<span data-ttu-id="606f1-127">Por exemplo, para usar a compilação de código aberto não oficial, `SQLCipher` use os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="606f1-127">For example, to use the unofficial, open-source build of `SQLCipher` use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="606f1-128">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="606f1-128">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="606f1-129">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="606f1-129">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a><span data-ttu-id="606f1-130">Provedores SQLitePCLRaw disponíveis</span><span class="sxs-lookup"><span data-stu-id="606f1-130">SQLitePCLRaw available providers</span></span>

<span data-ttu-id="606f1-131">Quando não depender de um pacote, você pode usar os provedores disponíveis do SQLite com o assembly principal.</span><span class="sxs-lookup"><span data-stu-id="606f1-131">When not relying on a bundle, you can use the available providers of SQLite with the core assembly.</span></span>

| <span data-ttu-id="606f1-132">Provedor</span><span class="sxs-lookup"><span data-stu-id="606f1-132">Provider</span></span> | <span data-ttu-id="606f1-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="606f1-133">Description</span></span> |
|--|--|
| [<span data-ttu-id="606f1-134">SQLitePCLRaw. Provider. Dynamic</span><span class="sxs-lookup"><span data-stu-id="606f1-134">SQLitePCLRaw.provider.dynamic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | <span data-ttu-id="606f1-135">O `dynamic` provedor carrega a biblioteca nativa em vez de usar <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> atributos.</span><span class="sxs-lookup"><span data-stu-id="606f1-135">The `dynamic` provider loads the native library instead of using <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributes.</span></span> <span data-ttu-id="606f1-136">Para obter mais informações sobre como usar esse provedor, consulte [usar o provedor dinâmico](#use-the-dynamic-provider).</span><span class="sxs-lookup"><span data-stu-id="606f1-136">For more information on using this provider, see [use the dynamic provider](#use-the-dynamic-provider).</span></span> |
| [<span data-ttu-id="606f1-137">SQLitePCLRaw. Provider. e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="606f1-137">SQLitePCLRaw.provider.e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | <span data-ttu-id="606f1-138">O `e_sqlite3` é o provedor padrão.</span><span class="sxs-lookup"><span data-stu-id="606f1-138">The `e_sqlite3` is the default provider.</span></span> |
| [<span data-ttu-id="606f1-139">SQLitePCLRaw. Provider. e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="606f1-139">SQLitePCLRaw.provider.e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | <span data-ttu-id="606f1-140">O `e_sqlcipher` provedor é o não oficial e não tem suporte `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="606f1-140">The `e_sqlcipher` provider is the unofficial and unsupported `SQLCipher`.</span></span> |
| [<span data-ttu-id="606f1-141">SQLitePCLRaw. Provider. sqlite3</span><span class="sxs-lookup"><span data-stu-id="606f1-141">SQLitePCLRaw.provider.sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | <span data-ttu-id="606f1-142">O `sqlite3` provedor é fornecido pelo sistema `SQLite` para IOS, MacOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="606f1-142">The `sqlite3` provider is a system-provided `SQLite` for iOS, macOS, and Linux.</span></span> |
| [<span data-ttu-id="606f1-143">SQLitePCLRaw. Provider. sqlcipher</span><span class="sxs-lookup"><span data-stu-id="606f1-143">SQLitePCLRaw.provider.sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | <span data-ttu-id="606f1-144">O `sqlcipher` provedor é para `SQLCipher` compilações oficiais do `Zetetic` .</span><span class="sxs-lookup"><span data-stu-id="606f1-144">The `sqlcipher` provider is for official `SQLCipher` builds from `Zetetic`.</span></span> |
| [<span data-ttu-id="606f1-145">SQLitePCLRaw. Provider. winsqlite3</span><span class="sxs-lookup"><span data-stu-id="606f1-145">SQLitePCLRaw.provider.winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | <span data-ttu-id="606f1-146">O `winsqlite3` provedor é para ambientes Windows 10.</span><span class="sxs-lookup"><span data-stu-id="606f1-146">The `winsqlite3` provider is for Windows 10 environments.</span></span> |

<span data-ttu-id="606f1-147">Para usar o `sqlite3` provedor, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="606f1-147">To use the `sqlite3` provider use the following commands:</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="606f1-148">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="606f1-148">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[<span data-ttu-id="606f1-149">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="606f1-149">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

<span data-ttu-id="606f1-150">Com os pacotes instalados, você define o provedor como a `sqlite3` instância.</span><span class="sxs-lookup"><span data-stu-id="606f1-150">With the packages installed, you then set the provider to the `sqlite3` instance.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a><span data-ttu-id="606f1-151">Usar o provedor dinâmico</span><span class="sxs-lookup"><span data-stu-id="606f1-151">Use the dynamic provider</span></span>

<span data-ttu-id="606f1-152">Você pode usar sua própria compilação do SQLite aproveitando o `SQLitePCLRaw.provider.dynamic_cdecl` pacote.</span><span class="sxs-lookup"><span data-stu-id="606f1-152">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="606f1-153">Nesse caso, você é responsável por implantar a biblioteca nativa com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="606f1-153">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="606f1-154">Observe que os detalhes da implantação de bibliotecas nativas com seu aplicativo variam consideravelmente dependendo da plataforma .NET e do tempo de execução que você está usando.</span><span class="sxs-lookup"><span data-stu-id="606f1-154">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="606f1-155">Primeiro, você precisará implementar `IGetFunctionPointer` .</span><span class="sxs-lookup"><span data-stu-id="606f1-155">First, you'll need to implement `IGetFunctionPointer`.</span></span> <span data-ttu-id="606f1-156">A implementação no .NET Core é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="606f1-156">The implementation on .NET Core is as follows:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="606f1-157">Em seguida, configure o `SQLitePCLRaw` provedor.</span><span class="sxs-lookup"><span data-stu-id="606f1-157">Next, configure the `SQLitePCLRaw` provider.</span></span> <span data-ttu-id="606f1-158">Verifique se isso é feito antes `Microsoft.Data.Sqlite` de ser usado em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="606f1-158">Ensure this is done before `Microsoft.Data.Sqlite` is used in your app.</span></span> <span data-ttu-id="606f1-159">Além disso, evite usar um `SQLitePCLRaw` pacote de pacotes que possa substituir seu provedor.</span><span class="sxs-lookup"><span data-stu-id="606f1-159">Also, avoid using a `SQLitePCLRaw` bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
