---
ms.openlocfilehash: 6c2aff4abf558307d599ff7533c82286e037bc71
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406136"
---
### <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a><span data-ttu-id="41811-101">APIs de System. Security. Cryptography não têm suporte no Webassembly de mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="41811-101">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>

<span data-ttu-id="41811-102"><xref:System.Security.Cryptography> As APIs lançam a <xref:System.PlatformNotSupportedException> em tempo de execução quando executadas em um navegador.</span><span class="sxs-lookup"><span data-stu-id="41811-102"><xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> at run time when run on a browser.</span></span>

#### <a name="change-description"></a><span data-ttu-id="41811-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="41811-103">Change description</span></span>

<span data-ttu-id="41811-104">Nas versões anteriores do .NET, a maioria das <xref:System.Security.Cryptography> APIs não está disponível para aplicativos Webassembly mais incrivelmente.</span><span class="sxs-lookup"><span data-stu-id="41811-104">In previous .NET versions, most of the <xref:System.Security.Cryptography> APIs aren't available to Blazor WebAssembly apps.</span></span> <span data-ttu-id="41811-105">A partir do .NET 5,0, os aplicativos Webassembly mais completos têm como destino a área completa da superfície da API do .NET 5, no entanto, nem todas as APIs do .NET 5 têm suporte devido a restrições de área restrita do navegador.</span><span class="sxs-lookup"><span data-stu-id="41811-105">Starting in .NET 5.0, Blazor WebAssembly apps target the full .NET 5 API surface area, however, not all .NET 5 APIs are supported due to browser sandbox constraints.</span></span> <span data-ttu-id="41811-106">No .NET 5,0 e versões posteriores, as APIs sem suporte <xref:System.Security.Cryptography> lançam um <xref:System.PlatformNotSupportedException> quando executado no Webassembly.</span><span class="sxs-lookup"><span data-stu-id="41811-106">In .NET 5.0 and later versions, the unsupported <xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> when running on WebAssembly.</span></span>

> [!TIP]
> <span data-ttu-id="41811-107">O [analisador de compatibilidade de plataforma](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) sinalizará todas as chamadas para as APIs afetadas quando você criar um projeto que dê suporte à plataforma do navegador.</span><span class="sxs-lookup"><span data-stu-id="41811-107">The [Platform compatibility analyzer](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) will flag any calls to the affected APIs when you build a project that supports the browser platform.</span></span> <span data-ttu-id="41811-108">Esse analisador é executado por padrão no .NET 5,0 e em aplicativos posteriores.</span><span class="sxs-lookup"><span data-stu-id="41811-108">This analyzer runs by default in .NET 5.0 and later apps.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="41811-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="41811-109">Reason for change</span></span>

<span data-ttu-id="41811-110">A Microsoft não pode enviar o OpenSSL como uma dependência na configuração de Webassembly mais incrivelmente.</span><span class="sxs-lookup"><span data-stu-id="41811-110">Microsoft is unable to ship OpenSSL as a dependency in the Blazor WebAssembly configuration.</span></span> <span data-ttu-id="41811-111">Tentamos solucionar isso tentando integrar com a API do navegador `SubtleCrypto` .</span><span class="sxs-lookup"><span data-stu-id="41811-111">We attempted to work around this by trying to integrate with the browser's `SubtleCrypto` API.</span></span> <span data-ttu-id="41811-112">Infelizmente, isso exigiu alterações significativas na API que tornaram muito difícil a integração.</span><span class="sxs-lookup"><span data-stu-id="41811-112">Unfortunately, it required significant API changes that made it too hard to integrate.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="41811-113">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="41811-113">Version introduced</span></span>

<span data-ttu-id="41811-114">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="41811-114">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="41811-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="41811-115">Recommended action</span></span>

<span data-ttu-id="41811-116">Não há boas soluções alternativas a serem sugeridas no momento.</span><span class="sxs-lookup"><span data-stu-id="41811-116">There are no good workarounds to suggest at this time.</span></span>

#### <a name="category"></a><span data-ttu-id="41811-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="41811-117">Category</span></span>

- <span data-ttu-id="41811-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="41811-118">ASP.NET Core</span></span>
- <span data-ttu-id="41811-119">Criptografia</span><span class="sxs-lookup"><span data-stu-id="41811-119">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="41811-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="41811-120">Affected APIs</span></span>

<span data-ttu-id="41811-121">Todas as <xref:System.Security.Cryptography?displayProperty=fullName> APIs, exceto as seguintes:</span><span class="sxs-lookup"><span data-stu-id="41811-121">All <xref:System.Security.Cryptography?displayProperty=fullName> APIs except the following:</span></span>

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

#### Affected APIs

- `T:System.Security.Cryptography`

-->
