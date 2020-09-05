---
ms.openlocfilehash: 14581b193fc000c7f805a0602e191cad688c014a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496950"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="bbe92-101">O calendário persa agora usa o algoritmo solar islâmico</span><span class="sxs-lookup"><span data-stu-id="bbe92-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="bbe92-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="bbe92-102">Details</span></span>

<span data-ttu-id="bbe92-103">A partir do .NET Framework 4.6, a classe <xref:System.Globalization.PersianCalendar?displayProperty=fullName> usa o algoritmo solar islâmico.</span><span class="sxs-lookup"><span data-stu-id="bbe92-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="bbe92-104">Converter datas entre o <xref:System.Globalization.PersianCalendar?displayProperty=fullName> e outros calendários pode produzir um resultado um pouco diferente começando com o .NET Framework 4.6 para datas anteriores a 1800 ou posteriores a 2023 (gregoriano). Além disso, agora <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> é <code>March 22, 0622</code> em vez de <code>March 21, 0622</code>.</span><span class="sxs-lookup"><span data-stu-id="bbe92-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bbe92-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="bbe92-105">Suggestion</span></span>

<span data-ttu-id="bbe92-106">Lembre-se de que algumas datas anteriores ou posteriores podem ser um pouco diferentes quando se usa o PersianCalendar no .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="bbe92-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="bbe92-107">Além disso, ao serializar datas entre processos que podem ser executados em diferentes versões do .NET Framework, não armazene-as como cadeias de caracteres de data PersianCalendar (uma vez que esses valores podem ser diferentes).</span><span class="sxs-lookup"><span data-stu-id="bbe92-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="bbe92-108">Nome</span><span class="sxs-lookup"><span data-stu-id="bbe92-108">Name</span></span>    | <span data-ttu-id="bbe92-109">Valor</span><span class="sxs-lookup"><span data-stu-id="bbe92-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bbe92-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="bbe92-110">Scope</span></span>   |<span data-ttu-id="bbe92-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="bbe92-111">Minor</span></span>|
|<span data-ttu-id="bbe92-112">Versão</span><span class="sxs-lookup"><span data-stu-id="bbe92-112">Version</span></span>|<span data-ttu-id="bbe92-113">4.6</span><span class="sxs-lookup"><span data-stu-id="bbe92-113">4.6</span></span>|
|<span data-ttu-id="bbe92-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="bbe92-114">Type</span></span>|<span data-ttu-id="bbe92-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="bbe92-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="bbe92-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="bbe92-116">Affected APIs</span></span>

- <xref:System.Globalization.PersianCalendar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Globalization.PersianCalendar`

-->
