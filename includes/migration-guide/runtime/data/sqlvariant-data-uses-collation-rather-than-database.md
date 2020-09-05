---
ms.openlocfilehash: fb339fb35cdcbba4f1c860fae9c17162c4cff596
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496703"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="e115c-101">Os dados do Sql_variant usam a ordenação sql_variant em vez da ordenação de banco de dados</span><span class="sxs-lookup"><span data-stu-id="e115c-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="e115c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e115c-102">Details</span></span>

<span data-ttu-id="e115c-103">Os dados do <code>sql_variant</code> usam a ordenação <code>sql_variant</code> em vez da ordenação de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e115c-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e115c-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e115c-104">Suggestion</span></span>

<span data-ttu-id="e115c-105">Essa alteração aborda os possíveis dados corrompidos caso a ordenação do banco de dados seja diferente da ordenação <code>sql_variant</code>.</span><span class="sxs-lookup"><span data-stu-id="e115c-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="e115c-106">Os aplicativos que dependem de dados corrompidos podem apresentar falhas.</span><span class="sxs-lookup"><span data-stu-id="e115c-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="e115c-107">Nome</span><span class="sxs-lookup"><span data-stu-id="e115c-107">Name</span></span>    | <span data-ttu-id="e115c-108">Valor</span><span class="sxs-lookup"><span data-stu-id="e115c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e115c-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="e115c-109">Scope</span></span>   |<span data-ttu-id="e115c-110">Transparente</span><span class="sxs-lookup"><span data-stu-id="e115c-110">Transparent</span></span>|
|<span data-ttu-id="e115c-111">Versão</span><span class="sxs-lookup"><span data-stu-id="e115c-111">Version</span></span>|<span data-ttu-id="e115c-112">4.5</span><span class="sxs-lookup"><span data-stu-id="e115c-112">4.5</span></span>|
|<span data-ttu-id="e115c-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="e115c-113">Type</span></span>|<span data-ttu-id="e115c-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="e115c-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e115c-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e115c-115">Affected APIs</span></span>

<span data-ttu-id="e115c-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="e115c-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
