---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621029"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="f2900-101">O calendário persa agora usa o algoritmo solar islâmico</span><span class="sxs-lookup"><span data-stu-id="f2900-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="f2900-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f2900-102">Details</span></span>

<span data-ttu-id="f2900-103">A partir do .NET Framework 4.6, a classe <xref:System.Globalization.PersianCalendar?displayProperty=fullName> usa o algoritmo solar islâmico.</span><span class="sxs-lookup"><span data-stu-id="f2900-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="f2900-104">Converter datas entre o <xref:System.Globalization.PersianCalendar?displayProperty=fullName> e outros calendários pode produzir um resultado um pouco diferente começando com o .NET Framework 4.6 para datas anteriores a 1800 ou posteriores a 2023 (gregoriano). Além disso, agora <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> é <code>March 22, 0622</code> em vez de <code>March 21, 0622</code>.</span><span class="sxs-lookup"><span data-stu-id="f2900-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f2900-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f2900-105">Suggestion</span></span>

<span data-ttu-id="f2900-106">Lembre-se de que algumas datas anteriores ou posteriores podem ser um pouco diferentes quando se usa o PersianCalendar no .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="f2900-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="f2900-107">Além disso, ao serializar datas entre processos que podem ser executados em diferentes versões do .NET Framework, não armazene-as como cadeias de caracteres de data PersianCalendar (uma vez que esses valores podem ser diferentes).</span><span class="sxs-lookup"><span data-stu-id="f2900-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="f2900-108">Name</span><span class="sxs-lookup"><span data-stu-id="f2900-108">Name</span></span>    | <span data-ttu-id="f2900-109">Valor</span><span class="sxs-lookup"><span data-stu-id="f2900-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f2900-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="f2900-110">Scope</span></span>   |<span data-ttu-id="f2900-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="f2900-111">Minor</span></span>|
|<span data-ttu-id="f2900-112">Versão</span><span class="sxs-lookup"><span data-stu-id="f2900-112">Version</span></span>|<span data-ttu-id="f2900-113">4.6</span><span class="sxs-lookup"><span data-stu-id="f2900-113">4.6</span></span>|
|<span data-ttu-id="f2900-114">Type</span><span class="sxs-lookup"><span data-stu-id="f2900-114">Type</span></span>|<span data-ttu-id="f2900-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="f2900-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f2900-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f2900-116">Affected APIs</span></span>

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
