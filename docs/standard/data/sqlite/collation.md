---
title: Collation
ms.date: 12/13/2019
description: Aprenda a criar uma seqüência de colagem personalizada.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242966"
---
# <a name="collation"></a><span data-ttu-id="a6be3-103">Collation</span><span class="sxs-lookup"><span data-stu-id="a6be3-103">Collation</span></span>

<span data-ttu-id="a6be3-104">As seqüências de coletâneas são usadas pelo SQLite ao comparar valores de TEXTO para determinar a ordem e a igualdade.</span><span class="sxs-lookup"><span data-stu-id="a6be3-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="a6be3-105">Você pode especificar qual colagem usar ao criar colunas ou por operação em consultas SQL.</span><span class="sxs-lookup"><span data-stu-id="a6be3-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="a6be3-106">O SQLite inclui três seqüências de colisão por padrão.</span><span class="sxs-lookup"><span data-stu-id="a6be3-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="a6be3-107">Collation</span><span class="sxs-lookup"><span data-stu-id="a6be3-107">Collation</span></span> | <span data-ttu-id="a6be3-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6be3-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="a6be3-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="a6be3-109">RTRIM</span></span>     | <span data-ttu-id="a6be3-110">Ignora o espaço branco em arrasto</span><span class="sxs-lookup"><span data-stu-id="a6be3-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="a6be3-111">NOCASE</span><span class="sxs-lookup"><span data-stu-id="a6be3-111">NOCASE</span></span>    | <span data-ttu-id="a6be3-112">Caso insensível para caracteres ASCII A-Z</span><span class="sxs-lookup"><span data-stu-id="a6be3-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="a6be3-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="a6be3-113">BINARY</span></span>    | <span data-ttu-id="a6be3-114">Sensível a casos.</span><span class="sxs-lookup"><span data-stu-id="a6be3-114">Case-sensitive.</span></span> <span data-ttu-id="a6be3-115">Compara bytes diretamente</span><span class="sxs-lookup"><span data-stu-id="a6be3-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="a6be3-116">Colagem personalizada</span><span class="sxs-lookup"><span data-stu-id="a6be3-116">Custom collation</span></span>

<span data-ttu-id="a6be3-117">Você também pode definir suas próprias seqüências de colisão ou substituir as incorporadas usando <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6be3-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="a6be3-118">O exemplo a seguir mostra sobrepondo a colagem NOCASE para suportar caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="a6be3-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="a6be3-119">O [código de amostra completo](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) está disponível no GitHub.</span><span class="sxs-lookup"><span data-stu-id="a6be3-119">The [full sample code](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="a6be3-120">Operador Like</span><span class="sxs-lookup"><span data-stu-id="a6be3-120">Like operator</span></span>

<span data-ttu-id="a6be3-121">O operador LIKE no SQLite não honra colagens.</span><span class="sxs-lookup"><span data-stu-id="a6be3-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="a6be3-122">A implementação padrão tem a mesma semântica que a colagem NOCASE.</span><span class="sxs-lookup"><span data-stu-id="a6be3-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="a6be3-123">É apenas caso insensível para os caracteres ASCII de A a Z.</span><span class="sxs-lookup"><span data-stu-id="a6be3-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="a6be3-124">Você pode facilmente tornar o operador LIKE sensível ao caso usando a seguinte declaração pragma:</span><span class="sxs-lookup"><span data-stu-id="a6be3-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="a6be3-125">Consulte [as funções definidas pelo usuário](user-defined-functions.md) para obter detalhes sobre a substituição da implementação do operador LIKE.</span><span class="sxs-lookup"><span data-stu-id="a6be3-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6be3-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="a6be3-126">See also</span></span>

* [<span data-ttu-id="a6be3-127">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="a6be3-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="a6be3-128">Sintaxe SQL</span><span class="sxs-lookup"><span data-stu-id="a6be3-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
