---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235051"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="e0726-101">Os dados do Sql_variant usam a ordenação sql_variant em vez da ordenação de banco de dados</span><span class="sxs-lookup"><span data-stu-id="e0726-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e0726-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e0726-102">Details</span></span>|<span data-ttu-id="e0726-103">Os dados do <code>sql_variant</code> usam a ordenação <code>sql_variant</code> em vez da ordenação de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e0726-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>|
|<span data-ttu-id="e0726-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e0726-104">Suggestion</span></span>|<span data-ttu-id="e0726-105">Essa alteração aborda os possíveis dados corrompidos caso a ordenação do banco de dados seja diferente da ordenação <code>sql_variant</code>.</span><span class="sxs-lookup"><span data-stu-id="e0726-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="e0726-106">Os aplicativos que dependem de dados corrompidos podem apresentar falhas.</span><span class="sxs-lookup"><span data-stu-id="e0726-106">Applications that rely on the corrupted data may experience failure.</span></span>|
|<span data-ttu-id="e0726-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="e0726-107">Scope</span></span>|<span data-ttu-id="e0726-108">Transparente</span><span class="sxs-lookup"><span data-stu-id="e0726-108">Transparent</span></span>|
|<span data-ttu-id="e0726-109">Versão</span><span class="sxs-lookup"><span data-stu-id="e0726-109">Version</span></span>|<span data-ttu-id="e0726-110">4.5</span><span class="sxs-lookup"><span data-stu-id="e0726-110">4.5</span></span>|
|<span data-ttu-id="e0726-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="e0726-111">Type</span></span>|<span data-ttu-id="e0726-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e0726-112">Runtime</span></span>|
