---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619792"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="5a860-101">Os dados do Sql_variant usam a ordenação sql_variant em vez da ordenação de banco de dados</span><span class="sxs-lookup"><span data-stu-id="5a860-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="5a860-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5a860-102">Details</span></span>

<span data-ttu-id="5a860-103">Os dados do <code>sql_variant</code> usam a ordenação <code>sql_variant</code> em vez da ordenação de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5a860-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5a860-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="5a860-104">Suggestion</span></span>

<span data-ttu-id="5a860-105">Essa alteração aborda os possíveis dados corrompidos caso a ordenação do banco de dados seja diferente da ordenação <code>sql_variant</code>.</span><span class="sxs-lookup"><span data-stu-id="5a860-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="5a860-106">Os aplicativos que dependem de dados corrompidos podem apresentar falhas.</span><span class="sxs-lookup"><span data-stu-id="5a860-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="5a860-107">Name</span><span class="sxs-lookup"><span data-stu-id="5a860-107">Name</span></span>    | <span data-ttu-id="5a860-108">Valor</span><span class="sxs-lookup"><span data-stu-id="5a860-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5a860-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="5a860-109">Scope</span></span>   |<span data-ttu-id="5a860-110">Transparente</span><span class="sxs-lookup"><span data-stu-id="5a860-110">Transparent</span></span>|
|<span data-ttu-id="5a860-111">Versão</span><span class="sxs-lookup"><span data-stu-id="5a860-111">Version</span></span>|<span data-ttu-id="5a860-112">4.5</span><span class="sxs-lookup"><span data-stu-id="5a860-112">4.5</span></span>|
|<span data-ttu-id="5a860-113">Type</span><span class="sxs-lookup"><span data-stu-id="5a860-113">Type</span></span>|<span data-ttu-id="5a860-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="5a860-114">Runtime</span></span>|
