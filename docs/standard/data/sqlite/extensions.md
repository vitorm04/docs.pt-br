---
title: Extensões do
ms.date: 12/13/2019
description: Saiba como carregar extensões do SQLite.
ms.openlocfilehash: ab00ccf31b8a22407fc177c18149fe4825a19091
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447254"
---
# <a name="extensions"></a><span data-ttu-id="d308e-103">Extensões do</span><span class="sxs-lookup"><span data-stu-id="d308e-103">Extensions</span></span>

<span data-ttu-id="d308e-104">O SQLite dá suporte ao carregamento de extensões em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d308e-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="d308e-105">As extensões incluem itens como funções SQL adicionais, agrupamentos, tabelas virtuais e muito mais.</span><span class="sxs-lookup"><span data-stu-id="d308e-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="d308e-106">O .NET Core inclui lógica adicional para a localização de bibliotecas nativas em locais adicionais, como pacotes NuGet referenciados.</span><span class="sxs-lookup"><span data-stu-id="d308e-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="d308e-107">Infelizmente, o SQLite não pode aproveitar essa lógica; Ele chama a API da plataforma diretamente para carregar bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="d308e-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="d308e-108">Por isso, seu aplicativo pode precisar modificar o caminho, LD_LIBRARY_PATH ou DYLD_LIBRARY_PATH variáveis de ambiente antes de carregar as extensões do SQLite.</span><span class="sxs-lookup"><span data-stu-id="d308e-108">Because of this, your app may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="d308e-109">Há [um exemplo](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) no GitHub que demonstra a localização de binários para o tempo de execução atual dentro de um pacote NuGet referenciado.</span><span class="sxs-lookup"><span data-stu-id="d308e-109">There's [a sample](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="d308e-110">Para carregar uma extensão, chame o método <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>.</span><span class="sxs-lookup"><span data-stu-id="d308e-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="d308e-111">Microsoft. Data. sqlite garantirá que a extensão permaneça carregada mesmo se a conexão for fechada e reaberta.</span><span class="sxs-lookup"><span data-stu-id="d308e-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a><span data-ttu-id="d308e-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="d308e-112">See also</span></span>

* [<span data-ttu-id="d308e-113">Extensões carregáveis de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d308e-113">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
