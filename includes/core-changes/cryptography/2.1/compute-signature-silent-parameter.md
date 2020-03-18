---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449202"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="c9a79-101">Parâmetro booleano de SignedCms.ComputeSignature é respeitado</span><span class="sxs-lookup"><span data-stu-id="c9a79-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="c9a79-102">No .NET Core, `silent` o parâmetro <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> booleano do método é respeitado.</span><span class="sxs-lookup"><span data-stu-id="c9a79-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="c9a79-103">Um prompt PIN não é mostrado se `true`este parâmetro estiver definido como .</span><span class="sxs-lookup"><span data-stu-id="c9a79-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c9a79-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="c9a79-104">Change description</span></span>

<span data-ttu-id="c9a79-105">No .NET Framework, o `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parâmetro do método é ignorado e um prompt PIN é sempre mostrado se necessário pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="c9a79-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="c9a79-106">No .NET Core, o `silent` parâmetro é respeitado `true`e, se definido como , um prompt PIN nunca é mostrado, mesmo que seja exigido pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="c9a79-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="c9a79-107">Suporte para CMS/PKCS #7 mensagens foi introduzida no .NET Core na versão 2.1.</span><span class="sxs-lookup"><span data-stu-id="c9a79-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c9a79-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c9a79-108">Version introduced</span></span>

<span data-ttu-id="c9a79-109">2.1</span><span class="sxs-lookup"><span data-stu-id="c9a79-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c9a79-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c9a79-110">Recommended action</span></span>

<span data-ttu-id="c9a79-111">Para garantir que um prompt PIN seja <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> exibido se necessário, os `false`aplicativos de desktop devem ligar e definir o parâmetro Boolean para .</span><span class="sxs-lookup"><span data-stu-id="c9a79-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="c9a79-112">O comportamento resultante é o mesmo do .NET Framework, independentemente de o contexto silencioso estar desativado lá.</span><span class="sxs-lookup"><span data-stu-id="c9a79-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="c9a79-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="c9a79-113">Category</span></span>

<span data-ttu-id="c9a79-114">Criptografia</span><span class="sxs-lookup"><span data-stu-id="c9a79-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="c9a79-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c9a79-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
