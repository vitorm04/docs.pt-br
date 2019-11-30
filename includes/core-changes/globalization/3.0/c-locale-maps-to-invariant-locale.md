---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567778"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="97de3-101">A localidade "C" é mapeada para a localidade invariável</span><span class="sxs-lookup"><span data-stu-id="97de3-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="97de3-102">O .NET Core 2,2 e versões anteriores dependem do comportamento padrão do ICU, que mapeia a localidade "C" para a localidade en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="97de3-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="97de3-103">A localidade en_US_POSIX tem um comportamento de agrupamento indesejável, pois não oferece suporte a comparações de cadeias de caracteres que não diferenciam maiúsculas de minúscula</span><span class="sxs-lookup"><span data-stu-id="97de3-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="97de3-104">Como algumas distribuições do Linux definem a localidade "C" como a localidade padrão, os usuários estão apresentando um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="97de3-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="97de3-105">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="97de3-105">Change description</span></span>

<span data-ttu-id="97de3-106">A partir do .NET Core 3,0, o mapeamento de localidade "C" foi alterado para usar a localidade invariável em vez de en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="97de3-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="97de3-107">A localidade "C" para mapeamento invariável também é aplicada ao Windows para fins de consistência.</span><span class="sxs-lookup"><span data-stu-id="97de3-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="97de3-108">O mapeamento de "C" para en_US_POSIX cultura causou confusão do cliente, porque en_US_POSIX não dá suporte a operações de cadeia de caracteres de classificação/pesquisa de maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="97de3-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="97de3-109">Como a localidade "C" é usada como uma localidade padrão em alguns dos distribuições do Linux, os clientes tiveram esse comportamento indesejado nesses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="97de3-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="97de3-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="97de3-110">Version introduced</span></span>

<span data-ttu-id="97de3-111">3.0</span><span class="sxs-lookup"><span data-stu-id="97de3-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="97de3-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="97de3-112">Recommended action</span></span>

<span data-ttu-id="97de3-113">Nada mais específico do que a conscientização dessa alteração.</span><span class="sxs-lookup"><span data-stu-id="97de3-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="97de3-114">Essa alteração afeta apenas os aplicativos que usam o mapeamento de localidade "C".</span><span class="sxs-lookup"><span data-stu-id="97de3-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="97de3-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="97de3-115">Category</span></span>

<span data-ttu-id="97de3-116">Globalização</span><span class="sxs-lookup"><span data-stu-id="97de3-116">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="97de3-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="97de3-117">Affected APIs</span></span>

<span data-ttu-id="97de3-118">Todas as APIs de agrupamento e cultura são afetadas por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="97de3-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
