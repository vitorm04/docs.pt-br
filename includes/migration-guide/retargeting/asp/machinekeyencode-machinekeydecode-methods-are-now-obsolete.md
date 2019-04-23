---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774287"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="27049-101">Os métodos MachineKey.Encode e MachineKey.Decode agora estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="27049-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="27049-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="27049-102">Details</span></span>|<span data-ttu-id="27049-103">Esses métodos são agora obsoletos.</span><span class="sxs-lookup"><span data-stu-id="27049-103">These methods are now obsolete.</span></span> <span data-ttu-id="27049-104">A compilação de código que chama estes métodos gera um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="27049-104">Compilation of code that calls these methods produces a compiler warning.</span></span>|
|<span data-ttu-id="27049-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="27049-105">Suggestion</span></span>|<span data-ttu-id="27049-106">As alternativas recomendadas são <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> e <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="27049-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="27049-107">Como alternativa, os avisos de compilação podem ser suprimidos ou evitados usando um compilador mais antigo.</span><span class="sxs-lookup"><span data-stu-id="27049-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="27049-108">Ainda há suporte para as APIs.</span><span class="sxs-lookup"><span data-stu-id="27049-108">The APIs are still supported.</span></span>|
|<span data-ttu-id="27049-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="27049-109">Scope</span></span>|<span data-ttu-id="27049-110">Secundário</span><span class="sxs-lookup"><span data-stu-id="27049-110">Minor</span></span>|
|<span data-ttu-id="27049-111">Versão</span><span class="sxs-lookup"><span data-stu-id="27049-111">Version</span></span>|<span data-ttu-id="27049-112">4.5</span><span class="sxs-lookup"><span data-stu-id="27049-112">4.5</span></span>|
|<span data-ttu-id="27049-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="27049-113">Type</span></span>|<span data-ttu-id="27049-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="27049-114">Retargeting</span></span>|
|<span data-ttu-id="27049-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="27049-115">Affected APIs</span></span>|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
