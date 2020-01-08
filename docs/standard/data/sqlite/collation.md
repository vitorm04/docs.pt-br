---
title: Ordenação
ms.date: 12/13/2019
description: Saiba como criar uma sequência de Agrupamento Personalizada.
ms.openlocfilehash: 0942ad4523a149ad74321cbe0f63021f53303579
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447023"
---
# <a name="collation"></a><span data-ttu-id="5d6b3-103">Ordenação</span><span class="sxs-lookup"><span data-stu-id="5d6b3-103">Collation</span></span>

<span data-ttu-id="5d6b3-104">As sequências de agrupamento são usadas pelo SQLite ao comparar valores de texto para determinar a ordem e a igualdade.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="5d6b3-105">Você pode especificar qual Agrupamento usar ao criar colunas ou por operação em consultas SQL.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="5d6b3-106">O SQLite inclui três sequências de agrupamento por padrão.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="5d6b3-107">Ordenação</span><span class="sxs-lookup"><span data-stu-id="5d6b3-107">Collation</span></span> | <span data-ttu-id="5d6b3-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d6b3-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="5d6b3-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="5d6b3-109">RTRIM</span></span>     | <span data-ttu-id="5d6b3-110">Ignora o espaço em branco à direita</span><span class="sxs-lookup"><span data-stu-id="5d6b3-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="5d6b3-111">NOCASESEMMAIÚSCMINÚSC</span><span class="sxs-lookup"><span data-stu-id="5d6b3-111">NOCASE</span></span>    | <span data-ttu-id="5d6b3-112">Não diferencia maiúsculas de minúsculas para caracteres ASCII de A-Z</span><span class="sxs-lookup"><span data-stu-id="5d6b3-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="5d6b3-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="5d6b3-113">BINARY</span></span>    | <span data-ttu-id="5d6b3-114">Diferenciar maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-114">Case-sensitive.</span></span> <span data-ttu-id="5d6b3-115">Compara bytes diretamente</span><span class="sxs-lookup"><span data-stu-id="5d6b3-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="5d6b3-116">Agrupamento personalizado</span><span class="sxs-lookup"><span data-stu-id="5d6b3-116">Custom collation</span></span>

<span data-ttu-id="5d6b3-117">Você também pode definir suas próprias sequências de agrupamento ou substituir as internas usando <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="5d6b3-118">O exemplo a seguir mostra a substituição do agrupamento nocase para dar suporte a caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="5d6b3-119">O [código de exemplo completo](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) está disponível no github.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-119">The [full sample code](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="5d6b3-120">Operador Like</span><span class="sxs-lookup"><span data-stu-id="5d6b3-120">Like operator</span></span>

<span data-ttu-id="5d6b3-121">O operador LIKE no SQLite não honra agrupamentos.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="5d6b3-122">A implementação padrão tem a mesma semântica que o agrupamento nocase.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="5d6b3-123">É apenas não diferencia maiúsculas de minúsculas para os caracteres ASCII de a a Z.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="5d6b3-124">Você pode facilmente tornar o operador LIKE com diferenciação de maiúsculas e minúsculas usando a seguinte instrução pragma:</span><span class="sxs-lookup"><span data-stu-id="5d6b3-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 0
```

<span data-ttu-id="5d6b3-125">Consulte [funções definidas pelo usuário](user-defined-functions.md) para obter detalhes sobre como substituir a implementação do operador Like.</span><span class="sxs-lookup"><span data-stu-id="5d6b3-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d6b3-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="5d6b3-126">See also</span></span>

* [<span data-ttu-id="5d6b3-127">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="5d6b3-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="5d6b3-128">Sintaxe SQL</span><span class="sxs-lookup"><span data-stu-id="5d6b3-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
