---
title: Extensões
ms.date: 12/13/2019
description: Aprenda a carregar extensões SQLite.
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242953"
---
# <a name="extensions"></a><span data-ttu-id="160a7-103">Extensões</span><span class="sxs-lookup"><span data-stu-id="160a7-103">Extensions</span></span>

<span data-ttu-id="160a7-104">O SQLite suporta extensões de carregamento em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="160a7-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="160a7-105">As extensões incluem coisas como funções SQL adicionais, colagens, tabelas virtuais e muito mais.</span><span class="sxs-lookup"><span data-stu-id="160a7-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="160a7-106">O .NET Core inclui lógica adicional para localizar bibliotecas nativas em lugares adicionais, como pacotes NuGet referenciados.</span><span class="sxs-lookup"><span data-stu-id="160a7-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="160a7-107">Infelizmente, o SQLite não pode aproveitar essa lógica; ele chama a API da plataforma diretamente para carregar bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="160a7-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="160a7-108">Por causa disso, você pode precisar modificar as variáveis de ambiente PATH, LD_LIBRARY_PATH ou DYLD_LIBRARY_PATH antes de carregar extensões SQLite.</span><span class="sxs-lookup"><span data-stu-id="160a7-108">Because of this, you may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="160a7-109">Há [uma amostra](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) no GitHub que demonstra encontrar binários para o tempo de execução atual dentro de um pacote NuGet referenciado.</span><span class="sxs-lookup"><span data-stu-id="160a7-109">There's [a sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="160a7-110">Para carregar uma extensão, ligue para o <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> método.</span><span class="sxs-lookup"><span data-stu-id="160a7-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="160a7-111">O Microsoft.Data.Sqlite garantirá que a extensão permaneça carregada mesmo que a conexão seja fechada e reaberta.</span><span class="sxs-lookup"><span data-stu-id="160a7-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a><span data-ttu-id="160a7-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="160a7-112">See also</span></span>

* [<span data-ttu-id="160a7-113">Extensões carregáveis em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="160a7-113">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
