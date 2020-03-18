---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567778"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="5a245-101">Mapas locais "C" para o local invariante</span><span class="sxs-lookup"><span data-stu-id="5a245-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="5a245-102">O .NET Core 2.2 e as versões anteriores dependem do comportamento padrão da UTI, que mapeia o local "C" para o local en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="5a245-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="5a245-103">O local en_US_POSIX tem um comportamento de colagem indesejável, porque não suporta comparações de seqüências insensíveis a casos.</span><span class="sxs-lookup"><span data-stu-id="5a245-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="5a245-104">Como algumas distribuições Linux definiram o local "C" como o local padrão, os usuários estavam experimentando um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="5a245-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5a245-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="5a245-105">Change description</span></span>

<span data-ttu-id="5a245-106">Começando com o .NET Core 3.0, o mapeamento local "C" foi alterado para usar o local Invariant em vez de en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="5a245-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="5a245-107">O mapeamento "C" para Invariant também é aplicado ao Windows para obter consistência.</span><span class="sxs-lookup"><span data-stu-id="5a245-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="5a245-108">O mapeamento de "C" para en_US_POSIX cultura causou confusão no cliente, porque en_US_POSIX não suporta operações de cadeias de classificação/pesquisa insensíveis.</span><span class="sxs-lookup"><span data-stu-id="5a245-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="5a245-109">Como o local "C" é usado como local padrão em algumas das distros do Linux, os clientes experimentaram esse comportamento indesejado nesses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="5a245-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5a245-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5a245-110">Version introduced</span></span>

<span data-ttu-id="5a245-111">3.0</span><span class="sxs-lookup"><span data-stu-id="5a245-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="5a245-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="5a245-112">Recommended action</span></span>

<span data-ttu-id="5a245-113">Nada específico mais do que a consciência desta mudança.</span><span class="sxs-lookup"><span data-stu-id="5a245-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="5a245-114">Essa alteração afeta apenas os aplicativos que usam o mapeamento local "C".</span><span class="sxs-lookup"><span data-stu-id="5a245-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="5a245-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="5a245-115">Category</span></span>

<span data-ttu-id="5a245-116">Globalização</span><span class="sxs-lookup"><span data-stu-id="5a245-116">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="5a245-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5a245-117">Affected APIs</span></span>

<span data-ttu-id="5a245-118">Todas as APIs de colagem e cultura são afetadas por essa mudança.</span><span class="sxs-lookup"><span data-stu-id="5a245-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
