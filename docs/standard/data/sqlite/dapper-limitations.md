---
title: Limitações do Dapper
ms.date: 12/13/2019
description: Descreve algumas das limitações que você encontrará ao usar o Dapper.
ms.openlocfilehash: 90c7fb24f068d663081390bdba9b1b222b4be56e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447275"
---
# <a name="dapper-limitations"></a><span data-ttu-id="5ef8e-103">Limitações do Dapper</span><span class="sxs-lookup"><span data-stu-id="5ef8e-103">Dapper limitations</span></span>

<span data-ttu-id="5ef8e-104">Há algumas limitações que você deve conhecer ao usar o Microsoft. Data. sqlite com [Dapper](https://stackexchange.github.io/Dapper/).</span><span class="sxs-lookup"><span data-stu-id="5ef8e-104">There are a few limitations you should be aware of when using Microsoft.Data.Sqlite with [Dapper](https://stackexchange.github.io/Dapper/).</span></span>

## <a name="parameters"></a><span data-ttu-id="5ef8e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ef8e-105">Parameters</span></span>

<span data-ttu-id="5ef8e-106">Os nomes de parâmetro do SQLite diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-106">SQLite parameter names are case-sensitive.</span></span> <span data-ttu-id="5ef8e-107">Verifique se os nomes de parâmetro usados no SQL correspondem ao caso das propriedades do objeto anônimo.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-107">Ensure that the parameter names used in SQL match the case of the anonymous object's properties.</span></span> <span data-ttu-id="5ef8e-108">O problema [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) melhoraria essa experiência.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-108">Issue [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) would improve this experience.</span></span>

<span data-ttu-id="5ef8e-109">Dapper também espera parâmetros para usar o prefixo `@`.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-109">Dapper also expects parameters to use the `@` prefix.</span></span> <span data-ttu-id="5ef8e-110">Outros prefixos não funcionarão.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-110">Other prefixes won't work.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a><span data-ttu-id="5ef8e-111">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5ef8e-111">Data types</span></span>

<span data-ttu-id="5ef8e-112">Dapper lê os valores usando o indexador SqliteDataReader.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-112">Dapper reads values using the SqliteDataReader indexer.</span></span> <span data-ttu-id="5ef8e-113">O tipo de retorno desse indexador é Object, o que significa que ele nunca retornará valores Long, Double, String ou byte [].</span><span class="sxs-lookup"><span data-stu-id="5ef8e-113">The return type of this indexer is object, which means it will only ever return long, double, string, or byte[] values.</span></span> <span data-ttu-id="5ef8e-114">Para obter mais informações, consulte [tipos de dados](types.md).</span><span class="sxs-lookup"><span data-stu-id="5ef8e-114">For more information, see [Data types](types.md).</span></span> <span data-ttu-id="5ef8e-115">O Dapper lida com a maioria das conversões entre esses e outros tipos primitivos.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-115">Dapper handles most conversions between these and other primitive types.</span></span> <span data-ttu-id="5ef8e-116">Infelizmente, ele não lida com `DateTimeOffset`, `Guid`ou `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-116">Unfortunately, it doesn't handle `DateTimeOffset`, `Guid`, or `TimeSpan`.</span></span> <span data-ttu-id="5ef8e-117">Crie manipuladores de tipo se você quiser usar esses tipos em seus resultados.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-117">Create type handlers if you want to use these types in your results.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

<span data-ttu-id="5ef8e-118">Não se esqueça de adicionar os manipuladores de tipo antes de consultar.</span><span class="sxs-lookup"><span data-stu-id="5ef8e-118">Don't forget to add the type handlers before querying.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a><span data-ttu-id="5ef8e-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="5ef8e-119">See also</span></span>

* [<span data-ttu-id="5ef8e-120">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5ef8e-120">Data types</span></span>](types.md)
* [<span data-ttu-id="5ef8e-121">Limitações assíncronas</span><span class="sxs-lookup"><span data-stu-id="5ef8e-121">Async limitations</span></span>](async.md)
