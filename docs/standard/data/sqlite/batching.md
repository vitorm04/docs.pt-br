---
title: Separação em lotes
ms.date: 12/13/2019
description: Saiba como executar um lote de instruções SQL em um único comando.
ms.openlocfilehash: 0799784471520bb279db6a4b5879ad30945bdebb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447051"
---
# <a name="batching"></a><span data-ttu-id="993ce-103">Separação em lotes</span><span class="sxs-lookup"><span data-stu-id="993ce-103">Batching</span></span>

<span data-ttu-id="993ce-104">O SQLite não dá suporte nativo a instruções SQL em lote em um único comando.</span><span class="sxs-lookup"><span data-stu-id="993ce-104">SQLite doesn't natively support batching SQL statements together into a single command.</span></span> <span data-ttu-id="993ce-105">Mas, como não há nenhuma rede envolvida, isso realmente ajudaria o desempenho mesmo assim.</span><span class="sxs-lookup"><span data-stu-id="993ce-105">But because there's no network involved, it wouldn't really help performance anyway.</span></span> <span data-ttu-id="993ce-106">O Microsoft. Data. sqlite, no entanto, implementa o envio em lote de instruções como uma conveniência para fazê-lo se comportar mais como outros provedores de ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="993ce-106">Microsoft.Data.Sqlite does, however, implement statement batching as a convenience to make it behave more like other ADO.NET providers.</span></span>

<span data-ttu-id="993ce-107">Ao chamar <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, as instruções são executadas até a primeira que retorna os resultados.</span><span class="sxs-lookup"><span data-stu-id="993ce-107">When calling <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, statements are executed up to the first one that returns results.</span></span> <span data-ttu-id="993ce-108">Chamar <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> continua executando instruções até o próximo que retorna resultados ou até atingir o final do lote.</span><span class="sxs-lookup"><span data-stu-id="993ce-108">Calling <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> continues executing statements until the next one that returns results or until it reaches the end of the batch.</span></span> <span data-ttu-id="993ce-109">Chamar <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> ou <xref:System.Data.Common.DbDataReader.Close%2A> executa quaisquer instruções restantes que não tenham sido consumidas pelo `NextResult()`.</span><span class="sxs-lookup"><span data-stu-id="993ce-109">Calling <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> or <xref:System.Data.Common.DbDataReader.Close%2A> executes any remaining statements that haven't been consumed by `NextResult()`.</span></span> <span data-ttu-id="993ce-110">Se você não descartar um leitor de dados, o finalizador tentará executar as instruções restantes, mas os erros encontrados serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="993ce-110">If you don't dispose a data reader, the finalizer tries to execute the remaining statements, but any errors it encounters are ignored.</span></span> <span data-ttu-id="993ce-111">Por isso, é importante descartar `DbDataReader` objetos ao usar lotes.</span><span class="sxs-lookup"><span data-stu-id="993ce-111">Because of this, it's important to dispose `DbDataReader` objects when using batches.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a><span data-ttu-id="993ce-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="993ce-112">See also</span></span>

* [<span data-ttu-id="993ce-113">Inserção em massa</span><span class="sxs-lookup"><span data-stu-id="993ce-113">Bulk Insert</span></span>](bulk-insert.md)
