---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235051"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a><span data-ttu-id="49f73-101">Os dados do Sql_variant usam a ordenação sql_variant em vez da ordenação de banco de dados</span><span class="sxs-lookup"><span data-stu-id="49f73-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="49f73-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="49f73-102">Details</span></span>|<code>sql_variant</code> <span data-ttu-id="49f73-103">Os dados usam a ordenação <code>sql_variant</code> em vez da ordenação de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="49f73-103">data uses <code>sql_variant</code> collation rather than database collation.</span></span>|
|<span data-ttu-id="49f73-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="49f73-104">Suggestion</span></span>|<span data-ttu-id="49f73-105">Essa alteração aborda os possíveis dados corrompidos caso a ordenação do banco de dados seja diferente da ordenação <code>sql_variant</code>.</span><span class="sxs-lookup"><span data-stu-id="49f73-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="49f73-106">Os aplicativos que dependem de dados corrompidos podem apresentar falhas.</span><span class="sxs-lookup"><span data-stu-id="49f73-106">Applications that rely on the corrupted data may experience failure.</span></span>|
|<span data-ttu-id="49f73-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="49f73-107">Scope</span></span>|<span data-ttu-id="49f73-108">Transparente</span><span class="sxs-lookup"><span data-stu-id="49f73-108">Transparent</span></span>|
|<span data-ttu-id="49f73-109">Versão</span><span class="sxs-lookup"><span data-stu-id="49f73-109">Version</span></span>|<span data-ttu-id="49f73-110">4.5</span><span class="sxs-lookup"><span data-stu-id="49f73-110">4.5</span></span>|
|<span data-ttu-id="49f73-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="49f73-111">Type</span></span>|<span data-ttu-id="49f73-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="49f73-112">Runtime</span></span>|
