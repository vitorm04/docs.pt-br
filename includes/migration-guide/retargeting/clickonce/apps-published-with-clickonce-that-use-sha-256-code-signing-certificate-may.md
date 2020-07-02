---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615590"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a><span data-ttu-id="1939d-101">Os aplicativos publicados com ClickOnce que usam um certificado de autenticação de código SHA-256 podem falhar no Windows 2003</span><span class="sxs-lookup"><span data-stu-id="1939d-101">Apps published with ClickOnce that use a SHA-256 code-signing certificate may fail on Windows 2003</span></span>

#### <a name="details"></a><span data-ttu-id="1939d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1939d-102">Details</span></span>

<span data-ttu-id="1939d-103">O executável é assinado com SHA256.</span><span class="sxs-lookup"><span data-stu-id="1939d-103">The executable is signed with SHA256.</span></span> <span data-ttu-id="1939d-104">Antes, ele era assinado com SHA1, independentemente se o certificado de assinatura de código era SHA-1 ou SHA-256.</span><span class="sxs-lookup"><span data-stu-id="1939d-104">Previously, it was signed with SHA1 regardless of whether the code-signing certificate was SHA-1 or SHA-256.</span></span> <span data-ttu-id="1939d-105">Isso se aplica a:</span><span class="sxs-lookup"><span data-stu-id="1939d-105">This applies to:</span></span>

- <span data-ttu-id="1939d-106">Todos os aplicativos compilados com o Visual Studio 2012 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="1939d-106">All applications built with Visual Studio 2012 or later.</span></span>
- <span data-ttu-id="1939d-107">Os aplicativos compilados com o Visual Studio 2010 ou anteriores em sistemas com o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="1939d-107">Applications built with Visual Studio 2010 or earlier on systems with the .NET Framework 4.5 present.</span></span>
<span data-ttu-id="1939d-108">Além disso, se o .NET Framework 4.5 ou posterior estiver presente, o manifesto do ClickOnce também será assinado com certificados SHA-256 para SHA-256, independentemente da versão do .NET Framework na qual ele foi compilado.</span><span class="sxs-lookup"><span data-stu-id="1939d-108">In addition, if the .NET Framework 4.5 or later is present, the ClickOnce manifest is also signed with SHA-256 for SHA-256 certificates regardless of the .NET Framework version against which it was compiled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1939d-109">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1939d-109">Suggestion</span></span>

<span data-ttu-id="1939d-110">A mudança na assinatura do executável do ClickOnce afeta apenas os sistemas Windows Server 2003; eles exigem a instalação do KB 938397.</span><span class="sxs-lookup"><span data-stu-id="1939d-110">The change in signing the ClickOnce executable affects only Windows Server 2003 systems; they require that KB 938397 be installed.</span></span> <span data-ttu-id="1939d-111">A alteração na assinatura do manifesto com SHA-256, mesmo quando um aplicativo destina-se ao .NET Framework 4.0 ou versões anteriores, introduz uma dependência de runtime no .NET Framework 4.5 ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="1939d-111">The change in signing the manifest with SHA-256 even when an app targets the .NET Framework 4.0 or earlier versions introduces a runtime dependency on the .NET Framework 4.5 or a later version.</span></span>

| <span data-ttu-id="1939d-112">Name</span><span class="sxs-lookup"><span data-stu-id="1939d-112">Name</span></span>    | <span data-ttu-id="1939d-113">Valor</span><span class="sxs-lookup"><span data-stu-id="1939d-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1939d-114">Escopo</span><span class="sxs-lookup"><span data-stu-id="1939d-114">Scope</span></span>   | <span data-ttu-id="1939d-115">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1939d-115">Edge</span></span>        |
| <span data-ttu-id="1939d-116">Versão</span><span class="sxs-lookup"><span data-stu-id="1939d-116">Version</span></span> | <span data-ttu-id="1939d-117">4.5</span><span class="sxs-lookup"><span data-stu-id="1939d-117">4.5</span></span>         |
| <span data-ttu-id="1939d-118">Type</span><span class="sxs-lookup"><span data-stu-id="1939d-118">Type</span></span>    | <span data-ttu-id="1939d-119">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="1939d-119">Retargeting</span></span> |
