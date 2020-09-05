---
ms.openlocfilehash: 3244913e06a744dafc4440f824ebe6bed25b8dd1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497463"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="72a52-101">ObjectDisposedException gerada pelo verificador ortográfico do WPF</span><span class="sxs-lookup"><span data-stu-id="72a52-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="72a52-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="72a52-102">Details</span></span>

<span data-ttu-id="72a52-103">Ocasionalmente, os aplicativos WPF falham durante o desligamento com uma <xref:System.ObjectDisposedException?displayProperty=fullName> gerada pelo verificador ortográfico.</span><span class="sxs-lookup"><span data-stu-id="72a52-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="72a52-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio do tratamento normal da exceção, garantindo que os aplicativos não sejam mais prejudicados.</span><span class="sxs-lookup"><span data-stu-id="72a52-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="72a52-105">Observe que exceções de primeira chance ocasionais continuariam a ser observadas em aplicativos em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="72a52-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="72a52-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="72a52-106">Suggestion</span></span>

<span data-ttu-id="72a52-107">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="72a52-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="72a52-108">Nome</span><span class="sxs-lookup"><span data-stu-id="72a52-108">Name</span></span>    | <span data-ttu-id="72a52-109">Valor</span><span class="sxs-lookup"><span data-stu-id="72a52-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="72a52-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="72a52-110">Scope</span></span>   |<span data-ttu-id="72a52-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="72a52-111">Edge</span></span>|
|<span data-ttu-id="72a52-112">Versão</span><span class="sxs-lookup"><span data-stu-id="72a52-112">Version</span></span>|<span data-ttu-id="72a52-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="72a52-113">4.6.1</span></span>|
|<span data-ttu-id="72a52-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="72a52-114">Type</span></span>|<span data-ttu-id="72a52-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="72a52-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="72a52-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="72a52-116">Affected APIs</span></span>

<span data-ttu-id="72a52-117">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="72a52-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
