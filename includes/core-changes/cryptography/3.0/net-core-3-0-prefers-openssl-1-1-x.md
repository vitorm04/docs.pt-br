---
ms.openlocfilehash: b49b2f88b130bb952b77964d5bf38374dc606385
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567962"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="7e32f-101">.NET Core 3.0 prefere OpenSSL 1.1.x ao OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="7e32f-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="7e32f-102">O .NET Core for Linux, que funciona em várias distribuições Linux, pode suportar tanto o OpenSSL 1.0.x quanto o OpenSSL 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="7e32f-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="7e32f-103">.NET Core 2.1 e .NET Core 2.2 olham para 1.0.x primeiro, depois recuam para 1.1.x; .NET Core 3.0 parece 1.1.x primeiro.</span><span class="sxs-lookup"><span data-stu-id="7e32f-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="7e32f-104">Essa mudança foi feita para adicionar suporte a novos padrões criptográficos.</span><span class="sxs-lookup"><span data-stu-id="7e32f-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="7e32f-105">Essa alteração pode impactar bibliotecas ou aplicativos que fazem interop de plataforma com os tipos de interop específicos do OpenSSL no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7e32f-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7e32f-106">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="7e32f-106">Change description</span></span>

<span data-ttu-id="7e32f-107">No .NET Core 2.2 e nas versões anteriores, o tempo de execução prefere carregar openssl 1.0.x sobre 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="7e32f-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="7e32f-108">Isso significa <xref:System.IntPtr> que <xref:System.Runtime.InteropServices.SafeHandle> os e os tipos para interop com OpenSSL são usados com libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 por preferência.</span><span class="sxs-lookup"><span data-stu-id="7e32f-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="7e32f-109">A partir do .NET Core 3.0, o tempo de execução prefere carregar openssl 1.1.x sobre OpenSSL 1.0.x, de modo que os <xref:System.IntPtr> e <xref:System.Runtime.InteropServices.SafeHandle> tipos para interop com OpenSSL são usados com libcrypto.so.1 / libcrypto.so.11 / libcrypto.so.1.1.1 / libcrypto.so.1 / libcrypto.so.1 por preferência.</span><span class="sxs-lookup"><span data-stu-id="7e32f-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="7e32f-110">Como resultado, bibliotecas e aplicativos que interoperam diretamente com o OpenSSL podem ter ponteiros incompatíveis com os valores expostos ao núcleo .NET ao atualizar do .NET Core 2.1 ou .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="7e32f-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7e32f-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7e32f-111">Version introduced</span></span>

<span data-ttu-id="7e32f-112">3.0</span><span class="sxs-lookup"><span data-stu-id="7e32f-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7e32f-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="7e32f-113">Recommended action</span></span>

<span data-ttu-id="7e32f-114">Bibliotecas e aplicativos que fazem operações diretas com o OpenSSL precisam ter cuidado para garantir que estejam usando a mesma versão do OpenSSL que o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7e32f-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="7e32f-115">Todas as bibliotecas ou <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> aplicativos que usam ou valorizam os tipos criptográficos .NET Core diretamente com <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> o OpenSSL devem comparar a versão da biblioteca que eles usam com a nova propriedade para garantir que os ponteiros sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="7e32f-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="7e32f-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="7e32f-116">Category</span></span>

<span data-ttu-id="7e32f-117">Criptografia</span><span class="sxs-lookup"><span data-stu-id="7e32f-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7e32f-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7e32f-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
