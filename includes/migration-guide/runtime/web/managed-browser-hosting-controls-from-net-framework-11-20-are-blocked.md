---
ms.openlocfilehash: 83d3f24680531d1e447f047151a28c98ce0da04b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619871"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="eba48-101">Controles de host do navegador gerenciado do .NET Framework 1.1 e 2.0 estão bloqueados</span><span class="sxs-lookup"><span data-stu-id="eba48-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

#### <a name="details"></a><span data-ttu-id="eba48-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="eba48-102">Details</span></span>

<span data-ttu-id="eba48-103">Hospedar esses controles é bloqueado no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="eba48-103">Hosting these controls is blocked in Internet Explorer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="eba48-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="eba48-104">Suggestion</span></span>

<span data-ttu-id="eba48-105">O Internet Explorer falhará ao iniciar um aplicativo que usa o navegador gerenciado que hospeda controles.</span><span class="sxs-lookup"><span data-stu-id="eba48-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="eba48-106">O comportamento anterior pode ser restaurado definindo o valor EnableIEHosting da subchave do registro <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> para <code>1</code> para sistemas x86 e para processos de 32 bits em sistemas de x64, e definindo o valor <code>EnableIEHosting</code> da subchave do registro <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> para <code>1</code> para processos de 64 bits em sistemas de x64.</span><span class="sxs-lookup"><span data-stu-id="eba48-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>

| <span data-ttu-id="eba48-107">Name</span><span class="sxs-lookup"><span data-stu-id="eba48-107">Name</span></span>    | <span data-ttu-id="eba48-108">Valor</span><span class="sxs-lookup"><span data-stu-id="eba48-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="eba48-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="eba48-109">Scope</span></span>   |<span data-ttu-id="eba48-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="eba48-110">Minor</span></span>|
|<span data-ttu-id="eba48-111">Versão</span><span class="sxs-lookup"><span data-stu-id="eba48-111">Version</span></span>|<span data-ttu-id="eba48-112">4.5</span><span class="sxs-lookup"><span data-stu-id="eba48-112">4.5</span></span>|
|<span data-ttu-id="eba48-113">Type</span><span class="sxs-lookup"><span data-stu-id="eba48-113">Type</span></span>|<span data-ttu-id="eba48-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="eba48-114">Runtime</span></span>|
