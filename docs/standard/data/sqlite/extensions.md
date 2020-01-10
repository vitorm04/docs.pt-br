---
title: Extensões do
ms.date: 12/13/2019
description: Saiba como carregar extensões do SQLite.
ms.openlocfilehash: 74b207205492bac48c89cb756470326f8e4a13c4
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777367"
---
# <a name="extensions"></a><span data-ttu-id="0fb79-103">Extensões do</span><span class="sxs-lookup"><span data-stu-id="0fb79-103">Extensions</span></span>

<span data-ttu-id="0fb79-104">O SQLite dá suporte ao carregamento de extensões em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0fb79-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="0fb79-105">As extensões incluem itens como funções SQL adicionais, agrupamentos, tabelas virtuais e muito mais.</span><span class="sxs-lookup"><span data-stu-id="0fb79-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="0fb79-106">O .NET Core inclui lógica adicional para a localização de bibliotecas nativas em locais adicionais, como pacotes NuGet referenciados.</span><span class="sxs-lookup"><span data-stu-id="0fb79-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="0fb79-107">Infelizmente, o SQLite não pode aproveitar essa lógica; Ele chama a API da plataforma diretamente para carregar bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="0fb79-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="0fb79-108">Por isso, seu aplicativo pode precisar modificar o caminho, LD_LIBRARY_PATH ou DYLD_LIBRARY_PATH variáveis de ambiente antes de carregar as extensões do SQLite.</span><span class="sxs-lookup"><span data-stu-id="0fb79-108">Because of this, your app may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="0fb79-109">Há [um exemplo](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) no GitHub que demonstra a localização de binários para o tempo de execução atual dentro de um pacote NuGet referenciado.</span><span class="sxs-lookup"><span data-stu-id="0fb79-109">There's [a sample](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="0fb79-110">Para carregar uma extensão, chame o método <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fb79-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="0fb79-111">Microsoft. Data. sqlite garantirá que a extensão permaneça carregada mesmo se a conexão for fechada e reaberta.</span><span class="sxs-lookup"><span data-stu-id="0fb79-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a><span data-ttu-id="0fb79-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="0fb79-112">See also</span></span>

* [<span data-ttu-id="0fb79-113">Extensões carregáveis de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0fb79-113">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
