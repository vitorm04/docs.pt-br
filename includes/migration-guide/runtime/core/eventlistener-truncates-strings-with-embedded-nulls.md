---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619779"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a><span data-ttu-id="7a227-101">EventListener trunca cadeias de caracteres com nulos inseridos</span><span class="sxs-lookup"><span data-stu-id="7a227-101">EventListener truncates strings with embedded nulls</span></span>

#### <a name="details"></a><span data-ttu-id="7a227-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7a227-102">Details</span></span>

<span data-ttu-id="7a227-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> trunca cadeias de caracteres com nulos inseridos.</span><span class="sxs-lookup"><span data-stu-id="7a227-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> truncates strings with embedded nulls.</span></span> <span data-ttu-id="7a227-104">Os caracteres nulos não são compatíveis com a classe <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="7a227-104">Null characters are not supported by the <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class.</span></span> <span data-ttu-id="7a227-105">A alteração afeta apenas os aplicativos que usam <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> para ler dados <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> no processo e que usam caracteres nulos como delimitadores.</span><span class="sxs-lookup"><span data-stu-id="7a227-105">The change only affects apps that use <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> to read <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process and that use null characters as delimiters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7a227-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7a227-106">Suggestion</span></span>

<span data-ttu-id="7a227-107">Os dados <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> devem ser atualizados, se possível, para não usar caracteres nulos inseridos.</span><span class="sxs-lookup"><span data-stu-id="7a227-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data should be updated, if possible, to not use embedded null characters.</span></span>

| <span data-ttu-id="7a227-108">Name</span><span class="sxs-lookup"><span data-stu-id="7a227-108">Name</span></span>    | <span data-ttu-id="7a227-109">Valor</span><span class="sxs-lookup"><span data-stu-id="7a227-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7a227-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="7a227-110">Scope</span></span>   |<span data-ttu-id="7a227-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7a227-111">Edge</span></span>|
|<span data-ttu-id="7a227-112">Versão</span><span class="sxs-lookup"><span data-stu-id="7a227-112">Version</span></span>|<span data-ttu-id="7a227-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7a227-113">4.5.1</span></span>|
|<span data-ttu-id="7a227-114">Type</span><span class="sxs-lookup"><span data-stu-id="7a227-114">Type</span></span>|<span data-ttu-id="7a227-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="7a227-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a227-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7a227-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
