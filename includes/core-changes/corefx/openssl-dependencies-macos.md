---
ms.openlocfilehash: 6a5cd260a2820e2a81142f6d55e32e91173ca503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147445"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="fa7bb-101">Versões openSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="fa7bb-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="fa7bb-102">O .NET Core 3.0 e os tempos de execução posteriores no macOS agora preferem versões OpenSSL <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>1.1.x para as versões OpenSSL 1.0.x para <xref:System.Security.Cryptography.RSAOpenSsl>os <xref:System.Security.Cryptography.SafeEvpPKeyHandle> <xref:System.Security.Cryptography.AesCcm>tipos , <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, e,</span><span class="sxs-lookup"><span data-stu-id="fa7bb-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="fa7bb-103">O tempo de execução do .NET Core 2.1 agora suporta versões OpenSSL 1.1.x, mas ainda prefere versões OpenSSL 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fa7bb-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="fa7bb-104">Change description</span></span>

<span data-ttu-id="fa7bb-105">Anteriormente, o tempo de execução do .NET Core usava versões OpenSSL 1.0.x no macOS para tipos que interagem com o OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="fa7bb-106">A versão mais recente do OpenSSL 1.0.x, OpenSSL 1.0.2, está agora sem suporte.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="fa7bb-107">Para manter os tipos que usam OpenSSL em versões suportadas do OpenSSL, o .NET Core 3.0 e os runtimes posteriores agora usam versões mais recentes do OpenSSL no macOS.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="fa7bb-108">Com essa mudança, o comportamento dos tempos de execução do .NET Core no macOS é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fa7bb-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="fa7bb-109">O .NET Core 3.0 e os runtimes posteriores da versão usam o OpenSSL 1.1.x, se disponível, e recuam para o OpenSSL 1.0.x apenas se não houver nenhuma versão 1.1.x disponível.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="fa7bb-110">Para os chamadores que usam os tipos de interop OpenSSL <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> com P/Invokes personalizados, siga as orientações nas observações.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="fa7bb-111">Seu aplicativo pode falhar se você <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> não verificar o valor.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="fa7bb-112">O tempo de execução do .NET Core 2.1 usa openssl 1.0.x, se disponível, e volta para openSSL 1.1.x se não houver nenhuma versão 1.0.x disponível.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="fa7bb-113">O tempo de execução 2.1 prefere a versão <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> anterior do OpenSSL porque a propriedade não existe no .NET Core 2.1, de modo que a versão OpenSSL não pode ser determinada de forma confiável no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fa7bb-114">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fa7bb-114">Version introduced</span></span>

- <span data-ttu-id="fa7bb-115">.NET Núcleo 2.1.16</span><span class="sxs-lookup"><span data-stu-id="fa7bb-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="fa7bb-116">.NET Núcleo 3.0.3</span><span class="sxs-lookup"><span data-stu-id="fa7bb-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="fa7bb-117">.NET Núcleo 3.1.2</span><span class="sxs-lookup"><span data-stu-id="fa7bb-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fa7bb-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fa7bb-118">Recommended action</span></span>

- <span data-ttu-id="fa7bb-119">Desinstale a versão 1.0.2 do OpenSSL se não for mais necessária.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="fa7bb-120">Instale o OpenSSL 1.1.x <xref:System.Security.Cryptography.DSAOpenSsl>se <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>você <xref:System.Security.Cryptography.RSAOpenSsl>usar <xref:System.Security.Cryptography.SafeEvpPKeyHandle> os <xref:System.Security.Cryptography.AesCcm>tipos , <xref:System.Security.Cryptography.AesGcm>, , ou , ou.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="fa7bb-121">Se você usar os tipos de interop OpenSSL com P/Invokes personalizados, siga as orientações nas <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> observações.</span><span class="sxs-lookup"><span data-stu-id="fa7bb-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="fa7bb-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="fa7bb-122">Category</span></span>

<span data-ttu-id="fa7bb-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="fa7bb-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fa7bb-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fa7bb-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
