---
title: Inserção em massa
ms.date: 12/13/2019
description: Dicas de desempenho que você pode usar ao fazer inúmeras alterações no banco de dados.
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447037"
---
# <a name="bulk-insert"></a><span data-ttu-id="3419c-103">Inserção em massa</span><span class="sxs-lookup"><span data-stu-id="3419c-103">Bulk insert</span></span>

<span data-ttu-id="3419c-104">O SQLite não tem nenhuma maneira especial para inserir dados em massa.</span><span class="sxs-lookup"><span data-stu-id="3419c-104">SQLite doesn't have any special way to bulk insert data.</span></span> <span data-ttu-id="3419c-105">Para obter o desempenho ideal ao inserir ou atualizar dados, certifique-se de fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3419c-105">To get optimal performance when inserting or updating data, ensure that you do the following:</span></span>

- <span data-ttu-id="3419c-106">Use uma transação.</span><span class="sxs-lookup"><span data-stu-id="3419c-106">Use a transaction.</span></span>
- <span data-ttu-id="3419c-107">Reutilize o mesmo comando com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3419c-107">Reuse the same parameterized command.</span></span> <span data-ttu-id="3419c-108">As execuções subsequentes reutilizarão a compilação da primeira.</span><span class="sxs-lookup"><span data-stu-id="3419c-108">Subsequent executions will reuse the compilation of the first one.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
