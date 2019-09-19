---
ms.openlocfilehash: 9e9e443be9ea51d214e95c676fc28f0d8790af8b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117179"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="4263c-101">A localidade "C" é mapeada para a localidade invariável</span><span class="sxs-lookup"><span data-stu-id="4263c-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="4263c-102">O .NET Core 2,2 e versões anteriores dependem do comportamento padrão do ICU, que mapeia a localidade "C" para a localidade en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="4263c-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="4263c-103">A localidade en_US_POSIX tem um comportamento de agrupamento indesejável, pois não oferece suporte a comparações de cadeias de caracteres que não diferenciam maiúsculas de minúscula</span><span class="sxs-lookup"><span data-stu-id="4263c-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="4263c-104">Como algumas distribuições do Linux definem a localidade "C" como a localidade padrão, os usuários estão apresentando um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="4263c-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span> 

#### <a name="details"></a><span data-ttu-id="4263c-105">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4263c-105">Details</span></span>

<span data-ttu-id="4263c-106">A partir do .NET Core 3,0, o mapeamento de localidade "C" foi alterado para usar a localidade invariável em vez de en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="4263c-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="4263c-107">A localidade "C" para mapeamento invariável também é aplicada ao Windows para fins de consistência.</span><span class="sxs-lookup"><span data-stu-id="4263c-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="4263c-108">O mapeamento de "C" para a cultura en_US_POSIX causou confusão do cliente, pois o en_US_POSIX não dá suporte a operações de cadeia de caracteres de classificação/pesquisa sem diferenciação</span><span class="sxs-lookup"><span data-stu-id="4263c-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="4263c-109">Como a localidade "C" é usada como uma localidade padrão em alguns dos distribuições do Linux, os clientes tiveram esse comportamento indesejado nesses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="4263c-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="4263c-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="4263c-110">Version introduced</span></span>

<span data-ttu-id="4263c-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4263c-111">.NET Core 3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="4263c-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="4263c-112">Recommended action</span></span>

<span data-ttu-id="4263c-113">Nada mais específico do que a conscientização dessa alteração.</span><span class="sxs-lookup"><span data-stu-id="4263c-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="4263c-114">Essa alteração afeta apenas os aplicativos que usam o mapeamento de localidade "C".</span><span class="sxs-lookup"><span data-stu-id="4263c-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="4263c-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="4263c-115">Category</span></span>

<span data-ttu-id="4263c-116">Globalização</span><span class="sxs-lookup"><span data-stu-id="4263c-116">Globalization</span></span> 

### <a name="affected-apis"></a><span data-ttu-id="4263c-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4263c-117">Affected APIs</span></span>

<span data-ttu-id="4263c-118">Todas as APIs de agrupamento e cultura são afetadas por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="4263c-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
