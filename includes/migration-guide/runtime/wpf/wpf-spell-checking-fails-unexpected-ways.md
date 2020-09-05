---
ms.openlocfilehash: d4e60f2a59980263916718ebcc71cc359952c031
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496254"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="3a931-101">A Verificação Ortográfica do WPF falha de formas inesperadas</span><span class="sxs-lookup"><span data-stu-id="3a931-101">WPF Spell Checking fails in unexpected ways</span></span>

#### <a name="details"></a><span data-ttu-id="3a931-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3a931-102">Details</span></span>

<span data-ttu-id="3a931-103">Isso inclui alguns problemas da Verificação Ortográfica do WPF:</span><span class="sxs-lookup"><span data-stu-id="3a931-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="3a931-104">Às vezes, a Verificação Ortográfica do WPF gera <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3a931-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span></span></li><li><span data-ttu-id="3a931-105">A Verificação Ortográfica do WPF falha com <xref:System.UnauthorizedAccessException> quando aplicativos são iniciados usando "Executar como usuário diferente"</span><span class="sxs-lookup"><span data-stu-id="3a931-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="3a931-106">O Verificador Ortográfico do WPF identifica incorretamente erros ortográficos em palavras compostas, como "Hausnummer" em alemão.</span><span class="sxs-lookup"><span data-stu-id="3a931-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="3a931-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="3a931-107">Suggestion</span></span>

<span data-ttu-id="3a931-108">Problema nº 1 – esse problema foi corrigido no .NET Framework 4.6.2 Problema nº 2 – a Verificação Ortográfica do WPF deixou de ter suporte quando aplicativos são iniciados usando "Executar como usuário diferente".</span><span class="sxs-lookup"><span data-stu-id="3a931-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="3a931-109">A partir do .NET Framework 4.6.2, aplicativos iniciados dessa maneira não falharão inesperadamente, em vez disso, a Verificação Ortográfica será desabilitada silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="3a931-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="3a931-110">Problema nº 3 – esse problema foi corrigido no .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="3a931-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="3a931-111">Nome</span><span class="sxs-lookup"><span data-stu-id="3a931-111">Name</span></span>    | <span data-ttu-id="3a931-112">Valor</span><span class="sxs-lookup"><span data-stu-id="3a931-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3a931-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="3a931-113">Scope</span></span>   |<span data-ttu-id="3a931-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="3a931-114">Edge</span></span>|
|<span data-ttu-id="3a931-115">Versão</span><span class="sxs-lookup"><span data-stu-id="3a931-115">Version</span></span>|<span data-ttu-id="3a931-116">4.6.1</span><span class="sxs-lookup"><span data-stu-id="3a931-116">4.6.1</span></span>|
|<span data-ttu-id="3a931-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="3a931-117">Type</span></span>|<span data-ttu-id="3a931-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="3a931-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3a931-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3a931-119">Affected APIs</span></span>

<span data-ttu-id="3a931-120">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="3a931-120">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
