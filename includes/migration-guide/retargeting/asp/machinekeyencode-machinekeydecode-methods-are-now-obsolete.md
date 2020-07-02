---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617104"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="02af9-101">Os métodos MachineKey.Encode e MachineKey.Decode agora estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="02af9-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="02af9-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="02af9-102">Details</span></span>

<span data-ttu-id="02af9-103">Esses métodos são agora obsoletos.</span><span class="sxs-lookup"><span data-stu-id="02af9-103">These methods are now obsolete.</span></span> <span data-ttu-id="02af9-104">A compilação de código que chama estes métodos gera um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="02af9-104">Compilation of code that calls these methods produces a compiler warning.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="02af9-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="02af9-105">Suggestion</span></span>

<span data-ttu-id="02af9-106">As alternativas recomendadas são <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> e <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="02af9-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="02af9-107">Como alternativa, os avisos de compilação podem ser suprimidos ou evitados usando um compilador mais antigo.</span><span class="sxs-lookup"><span data-stu-id="02af9-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="02af9-108">Ainda há suporte para as APIs.</span><span class="sxs-lookup"><span data-stu-id="02af9-108">The APIs are still supported.</span></span>

| <span data-ttu-id="02af9-109">Name</span><span class="sxs-lookup"><span data-stu-id="02af9-109">Name</span></span>    | <span data-ttu-id="02af9-110">Valor</span><span class="sxs-lookup"><span data-stu-id="02af9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="02af9-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="02af9-111">Scope</span></span>   | <span data-ttu-id="02af9-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="02af9-112">Minor</span></span>       |
| <span data-ttu-id="02af9-113">Versão</span><span class="sxs-lookup"><span data-stu-id="02af9-113">Version</span></span> | <span data-ttu-id="02af9-114">4.5</span><span class="sxs-lookup"><span data-stu-id="02af9-114">4.5</span></span>         |
| <span data-ttu-id="02af9-115">Type</span><span class="sxs-lookup"><span data-stu-id="02af9-115">Type</span></span>    | <span data-ttu-id="02af9-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="02af9-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="02af9-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="02af9-117">Affected APIs</span></span>

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
