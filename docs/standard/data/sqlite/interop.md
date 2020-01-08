---
title: Interoperabilidade
ms.date: 12/13/2019
description: Saiba como interoperar com outras bibliotecas do SQLite.
ms.openlocfilehash: 486e2a8e00999b8ebe9c85a5fcc1539c514676d3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447233"
---
# <a name="interoperability"></a><span data-ttu-id="da5f5-103">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="da5f5-103">Interoperability</span></span>

<span data-ttu-id="da5f5-104">Microsoft. Data. sqlite usa SQLitePCLRaw para interagir com a biblioteca SQLite nativa.</span><span class="sxs-lookup"><span data-stu-id="da5f5-104">Microsoft.Data.Sqlite uses SQLitePCLRaw to interact with the native SQLite library.</span></span> <span data-ttu-id="da5f5-105">O SQLitePCLRaw fornece uma API .NET fina sobre a API do SQLite nativo.</span><span class="sxs-lookup"><span data-stu-id="da5f5-105">SQLitePCLRaw provides a thin .NET API over the native SQLite API.</span></span> <span data-ttu-id="da5f5-106">SqliteConnection e SqliteDataReader fornecem acesso aos objetos SQLitePCLRaw subjacentes, permitindo que você chame essas APIs diretamente.</span><span class="sxs-lookup"><span data-stu-id="da5f5-106">SqliteConnection and SqliteDataReader provide access to the underlying SQLitePCLRaw objects letting you call these APIs directly.</span></span>

<span data-ttu-id="da5f5-107">O exemplo a seguir mostra como chamar `sqlite3_trace` para gravar instruções SQL executadas no console do:</span><span class="sxs-lookup"><span data-stu-id="da5f5-107">The following example shows how to call `sqlite3_trace` to write executed SQL statements to the console:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

<span data-ttu-id="da5f5-108">E o exemplo a seguir mostra a chamada de `sqlite3_stmt_status` para ver quantas etapas de máquina virtual do SQLite uma instrução SQL compilou em:</span><span class="sxs-lookup"><span data-stu-id="da5f5-108">And the following example shows calling `sqlite3_stmt_status` to see how many SQLite virtual machine steps a SQL statement compiled into:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

<span data-ttu-id="da5f5-109">Os objetos SQLitePCLRaw até expõem um ponteiro para os objetos nativos, permitindo P/Invoke APIs adicionais do SQLite nativo.</span><span class="sxs-lookup"><span data-stu-id="da5f5-109">The SQLitePCLRaw objects even expose a pointer to the native objects letting you P/Invoke additional native SQLite APIs.</span></span>
