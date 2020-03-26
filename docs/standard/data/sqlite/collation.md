---
title: Collation
ms.date: 12/13/2019
description: Aprenda a criar uma seqüência de colagem personalizada.
ms.openlocfilehash: b93c82a4ace154b8293b05effa8f9e9294fa7708
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506535"
---
# <a name="collation"></a><span data-ttu-id="02fe5-103">Collation</span><span class="sxs-lookup"><span data-stu-id="02fe5-103">Collation</span></span>

<span data-ttu-id="02fe5-104">As seqüências de coletâneas são usadas pelo SQLite ao comparar valores de TEXTO para determinar a ordem e a igualdade.</span><span class="sxs-lookup"><span data-stu-id="02fe5-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="02fe5-105">Você pode especificar qual colagem usar ao criar colunas ou por operação em consultas SQL.</span><span class="sxs-lookup"><span data-stu-id="02fe5-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="02fe5-106">O SQLite inclui três seqüências de colisão por padrão.</span><span class="sxs-lookup"><span data-stu-id="02fe5-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="02fe5-107">Collation</span><span class="sxs-lookup"><span data-stu-id="02fe5-107">Collation</span></span> | <span data-ttu-id="02fe5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="02fe5-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="02fe5-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="02fe5-109">RTRIM</span></span>     | <span data-ttu-id="02fe5-110">Ignora o espaço branco em arrasto</span><span class="sxs-lookup"><span data-stu-id="02fe5-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="02fe5-111">NOCASE</span><span class="sxs-lookup"><span data-stu-id="02fe5-111">NOCASE</span></span>    | <span data-ttu-id="02fe5-112">Caso insensível para caracteres ASCII A-Z</span><span class="sxs-lookup"><span data-stu-id="02fe5-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="02fe5-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="02fe5-113">BINARY</span></span>    | <span data-ttu-id="02fe5-114">Sensível a casos.</span><span class="sxs-lookup"><span data-stu-id="02fe5-114">Case-sensitive.</span></span> <span data-ttu-id="02fe5-115">Compara bytes diretamente</span><span class="sxs-lookup"><span data-stu-id="02fe5-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="02fe5-116">Colagem personalizada</span><span class="sxs-lookup"><span data-stu-id="02fe5-116">Custom collation</span></span>

<span data-ttu-id="02fe5-117">Você também pode definir suas próprias seqüências de colisão ou substituir as incorporadas usando <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="02fe5-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="02fe5-118">O exemplo a seguir mostra sobrepondo a colagem NOCASE para suportar caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="02fe5-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="02fe5-119">O [código de amostra completo](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) está disponível no GitHub.</span><span class="sxs-lookup"><span data-stu-id="02fe5-119">The [full sample code](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="02fe5-120">Operador Like</span><span class="sxs-lookup"><span data-stu-id="02fe5-120">Like operator</span></span>

<span data-ttu-id="02fe5-121">O operador LIKE no SQLite não honra colagens.</span><span class="sxs-lookup"><span data-stu-id="02fe5-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="02fe5-122">A implementação padrão tem a mesma semântica que a colagem NOCASE.</span><span class="sxs-lookup"><span data-stu-id="02fe5-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="02fe5-123">É apenas caso insensível para os caracteres ASCII de A a Z.</span><span class="sxs-lookup"><span data-stu-id="02fe5-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="02fe5-124">Você pode facilmente tornar o operador LIKE sensível ao caso usando a seguinte declaração pragma:</span><span class="sxs-lookup"><span data-stu-id="02fe5-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="02fe5-125">Consulte [as funções definidas pelo usuário](user-defined-functions.md) para obter detalhes sobre a substituição da implementação do operador LIKE.</span><span class="sxs-lookup"><span data-stu-id="02fe5-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="02fe5-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="02fe5-126">See also</span></span>

* [<span data-ttu-id="02fe5-127">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="02fe5-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="02fe5-128">Sintaxe SQL</span><span class="sxs-lookup"><span data-stu-id="02fe5-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
