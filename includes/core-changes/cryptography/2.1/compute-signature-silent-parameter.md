---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721466"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="a14ea-101">O parâmetro booliano de SignedCms. ComputeSignature é respeitado</span><span class="sxs-lookup"><span data-stu-id="a14ea-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="a14ea-102">No .NET Core, o parâmetro booliano `silent` do <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> método é respeitado.</span><span class="sxs-lookup"><span data-stu-id="a14ea-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="a14ea-103">Um prompt de PIN não será exibido se esse parâmetro for definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="a14ea-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a14ea-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="a14ea-104">Change description</span></span>

<span data-ttu-id="a14ea-105">No .NET Framework, o `silent` parâmetro do <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> método é ignorado e um prompt de PIN é sempre mostrado se exigido pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="a14ea-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="a14ea-106">No .NET Core, o `silent` parâmetro é respeitado e, se definido como `true` , um aviso de PIN nunca é mostrado, mesmo que seja exigido pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="a14ea-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="a14ea-107">O suporte para mensagens #7 CMS/PKCS foi introduzido no .NET Core na versão 2,1.</span><span class="sxs-lookup"><span data-stu-id="a14ea-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a14ea-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a14ea-108">Version introduced</span></span>

<span data-ttu-id="a14ea-109">2.1</span><span class="sxs-lookup"><span data-stu-id="a14ea-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a14ea-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a14ea-110">Recommended action</span></span>

<span data-ttu-id="a14ea-111">Para garantir que um prompt de PIN apareça se necessário, os aplicativos de área de trabalho devem chamar <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> e definir o parâmetro booliano como `false` .</span><span class="sxs-lookup"><span data-stu-id="a14ea-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="a14ea-112">O comportamento resultante é o mesmo que em .NET Framework, independentemente de o contexto silencioso estar desabilitado lá.</span><span class="sxs-lookup"><span data-stu-id="a14ea-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

#### <a name="category"></a><span data-ttu-id="a14ea-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="a14ea-113">Category</span></span>

<span data-ttu-id="a14ea-114">Criptografia</span><span class="sxs-lookup"><span data-stu-id="a14ea-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a14ea-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a14ea-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
