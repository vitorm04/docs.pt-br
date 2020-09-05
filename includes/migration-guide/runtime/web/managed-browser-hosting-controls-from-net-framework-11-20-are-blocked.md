---
ms.openlocfilehash: 26539011f0650c7a3bac9e1c41847561905fff58
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496239"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="83d3e-101">Controles de host do navegador gerenciado do .NET Framework 1.1 e 2.0 estão bloqueados</span><span class="sxs-lookup"><span data-stu-id="83d3e-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

#### <a name="details"></a><span data-ttu-id="83d3e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="83d3e-102">Details</span></span>

<span data-ttu-id="83d3e-103">Hospedar esses controles é bloqueado no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="83d3e-103">Hosting these controls is blocked in Internet Explorer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="83d3e-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="83d3e-104">Suggestion</span></span>

<span data-ttu-id="83d3e-105">O Internet Explorer falhará ao iniciar um aplicativo que usa o navegador gerenciado que hospeda controles.</span><span class="sxs-lookup"><span data-stu-id="83d3e-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="83d3e-106">O comportamento anterior pode ser restaurado definindo o valor EnableIEHosting da subchave do registro <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> para <code>1</code> para sistemas x86 e para processos de 32 bits em sistemas de x64, e definindo o valor <code>EnableIEHosting</code> da subchave do registro <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> para <code>1</code> para processos de 64 bits em sistemas de x64.</span><span class="sxs-lookup"><span data-stu-id="83d3e-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>

| <span data-ttu-id="83d3e-107">Nome</span><span class="sxs-lookup"><span data-stu-id="83d3e-107">Name</span></span>    | <span data-ttu-id="83d3e-108">Valor</span><span class="sxs-lookup"><span data-stu-id="83d3e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="83d3e-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="83d3e-109">Scope</span></span>   |<span data-ttu-id="83d3e-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="83d3e-110">Minor</span></span>|
|<span data-ttu-id="83d3e-111">Versão</span><span class="sxs-lookup"><span data-stu-id="83d3e-111">Version</span></span>|<span data-ttu-id="83d3e-112">4.5</span><span class="sxs-lookup"><span data-stu-id="83d3e-112">4.5</span></span>|
|<span data-ttu-id="83d3e-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="83d3e-113">Type</span></span>|<span data-ttu-id="83d3e-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="83d3e-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="83d3e-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="83d3e-115">Affected APIs</span></span>

<span data-ttu-id="83d3e-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="83d3e-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
