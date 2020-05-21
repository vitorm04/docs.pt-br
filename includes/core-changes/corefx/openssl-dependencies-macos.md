---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721161"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="40622-101">Versões do OpenSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="40622-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="40622-102">Os tempos de execução do .NET Core 3,0 e posteriores no MacOS agora preferem as versões do OpenSSL 1.1. x às versões do OpenSSL 1.0. x para os <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> tipos,, <xref:System.Security.Cryptography.DSAOpenSsl> , <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> ,, <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> e <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .</span><span class="sxs-lookup"><span data-stu-id="40622-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="40622-103">O tempo de execução do .NET Core 2,1 agora dá suporte às versões do OpenSSL 1.1. x, mas ainda prefere as versões do OpenSSL 1.0. x.</span><span class="sxs-lookup"><span data-stu-id="40622-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="40622-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="40622-104">Change description</span></span>

<span data-ttu-id="40622-105">Anteriormente, o tempo de execução do .NET Core usava as versões do OpenSSL 1.0. x no macOS para tipos que interagem com o OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="40622-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="40622-106">A versão mais recente do OpenSSL 1.0. x, OpenSSL 1.0.2, agora está sem suporte.</span><span class="sxs-lookup"><span data-stu-id="40622-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="40622-107">Para manter os tipos que usam o OpenSSL nas versões com suporte do OpenSSL, os tempos de execução do .NET Core 3,0 e posteriores agora usam versões mais recentes do OpenSSL no macOS.</span><span class="sxs-lookup"><span data-stu-id="40622-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="40622-108">Com essa alteração, o comportamento dos tempos de execução do .NET Core no macOS é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="40622-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="40622-109">Os tempos de execução do .NET Core 3,0 e versões posteriores usam o OpenSSL 1.1. x, se disponível, e retornarão ao OpenSSL 1.0. x somente se não houver nenhuma versão 1.1. x disponível.</span><span class="sxs-lookup"><span data-stu-id="40622-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="40622-110">Para chamadores que usam os tipos de interoperabilidade OpenSSL com P/Invokes personalizados, siga as orientações em <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> comentários.</span><span class="sxs-lookup"><span data-stu-id="40622-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="40622-111">Seu aplicativo poderá falhar se você não verificar o <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> valor.</span><span class="sxs-lookup"><span data-stu-id="40622-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="40622-112">O tempo de execução do .NET Core 2,1 usa o OpenSSL 1.0. x, se estiver disponível, e voltará ao OpenSSL 1.1. x se não houver nenhuma versão 1.0. x disponível.</span><span class="sxs-lookup"><span data-stu-id="40622-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="40622-113">O tempo de execução 2,1 prefere a versão anterior do OpenSSL porque a <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> propriedade não existe no .NET Core 2,1, portanto, a versão do OpenSSL não pode ser determinada de forma confiável no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="40622-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="40622-114">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="40622-114">Version introduced</span></span>

- <span data-ttu-id="40622-115">2.1.16 do .NET Core</span><span class="sxs-lookup"><span data-stu-id="40622-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="40622-116">3.0.3 do .NET Core</span><span class="sxs-lookup"><span data-stu-id="40622-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="40622-117">3.1.2 do .NET Core</span><span class="sxs-lookup"><span data-stu-id="40622-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="40622-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="40622-118">Recommended action</span></span>

- <span data-ttu-id="40622-119">Desinstale o OpenSSL versão 1.0.2 se ele não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="40622-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="40622-120">Instale o OpenSSL 1.1. x se você usar <xref:System.Security.Cryptography.AesCcm> os <xref:System.Security.Cryptography.AesGcm> tipos,,,,, <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> ou <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .</span><span class="sxs-lookup"><span data-stu-id="40622-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="40622-121">Se você usar os tipos de interoperabilidade OpenSSL com P/Invokes personalizados, siga as orientações em <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> comentários.</span><span class="sxs-lookup"><span data-stu-id="40622-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="40622-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="40622-122">Category</span></span>

<span data-ttu-id="40622-123">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="40622-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="40622-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="40622-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
