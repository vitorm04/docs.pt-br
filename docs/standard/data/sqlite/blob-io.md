---
title: E/s de BLOB
ms.date: 12/13/2019
description: Saiba como usar O recurso de e/s de BLOB do SQLite.
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447044"
---
# <a name="blob-io"></a><span data-ttu-id="2a8fa-103">E/s de BLOB</span><span class="sxs-lookup"><span data-stu-id="2a8fa-103">Blob I/O</span></span>

<span data-ttu-id="2a8fa-104">Você pode reduzir o uso de memória durante a leitura e a gravação de objetos grandes transmitindo os dados para dentro e fora dele.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-104">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="2a8fa-105">Isso pode ser especialmente útil ao analisar ou transformar os dados.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-105">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="2a8fa-106">Comece inserindo uma linha como normal.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-106">Start by inserting a row as normal.</span></span> <span data-ttu-id="2a8fa-107">Use a função `zeroblob()` SQL para alocar espaço no banco de dados para manter o objeto grande.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-107">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="2a8fa-108">A função `last_insert_rowid()` fornece uma maneira conveniente de obter seu ROWID.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-108">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="2a8fa-109">Depois de inserir a linha, abra um fluxo para gravar o objeto grande usando <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-109">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="2a8fa-110">Para transmitir o objeto grande para fora do banco de dados, você deve selecionar o ROWID ou um de seus aliases, como mostrado aqui, além da coluna do objeto grande.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-110">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="2a8fa-111">Se você não selecionar o ROWID, todo o objeto será carregado na memória.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-111">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="2a8fa-112">O objeto retornado por `GetStream()` será uma `SqliteBlob` quando feito corretamente.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-112">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
