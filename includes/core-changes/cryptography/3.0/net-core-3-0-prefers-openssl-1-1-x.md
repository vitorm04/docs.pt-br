---
ms.openlocfilehash: 877f9d99b660c4af843e4d8d525219c1df6c99a9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721458"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="2a9a4-101">O .NET Core 3,0 prefere o OpenSSL 1.1. x ao OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="2a9a4-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="2a9a4-102">O .NET Core para Linux, que funciona em várias distribuições do Linux, pode dar suporte a OpenSSL 1.0. x e OpenSSL 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="2a9a4-103">.NET Core 2,1 e .NET Core 2,2 Procure 1,0. x primeiro e, em seguida, retorne para 1.1. x; o .NET Core 3,0 procura por 1,1. x primeiro.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="2a9a4-104">Essa alteração foi feita para adicionar suporte para novos padrões de criptografia.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="2a9a4-105">Essa alteração pode afetar as bibliotecas ou os aplicativos que fazem a interoperabilidade de plataforma com os tipos de interoperabilidade específicos do OpenSSL no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2a9a4-106">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="2a9a4-106">Change description</span></span>

<span data-ttu-id="2a9a4-107">No .NET Core 2,2 e versões anteriores, o tempo de execução prefere carregar o OpenSSL 1.0. x acima de 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="2a9a4-108">Isso significa que os <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> tipos e para interoperabilidade com OpenSSL são usados com libcrypto. portanto. 1.0.0/libcrypto. portanto. 1.0/libcrypto. portanto, 10 por preferência.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="2a9a4-109">A partir do .NET Core 3,0, o tempo de execução prefere carregar o OpenSSL 1.1. x em relação ao OpenSSL 1.0. x, portanto, os <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> tipos e para interoperabilidade com OpenSSL são usados com libcrypto. por isso, 1.1/libcrypto. portanto, 11/libcrypto. portanto, 1.1.0/libcrypto. portanto, 1.1.1 por preferência.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="2a9a4-110">Como resultado, as bibliotecas e os aplicativos que interoperam com o OpenSSL diretamente podem ter ponteiros incompatíveis com os valores expostos do .NET Core ao atualizar do .NET Core 2,1 ou do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2a9a4-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="2a9a4-111">Version introduced</span></span>

<span data-ttu-id="2a9a4-112">3.0</span><span class="sxs-lookup"><span data-stu-id="2a9a4-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2a9a4-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="2a9a4-113">Recommended action</span></span>

<span data-ttu-id="2a9a4-114">Bibliotecas e aplicativos que fazem operações diretas com o OpenSSL precisam ter cuidado para garantir que estejam usando a mesma versão do OpenSSL que o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="2a9a4-115">Todas as bibliotecas ou aplicativos que usam <xref:System.IntPtr> ou <xref:System.Runtime.InteropServices.SafeHandle> valores dos tipos de criptografia do .NET Core diretamente com o OpenSSL devem comparar a versão da biblioteca que usam com a nova <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> propriedade para garantir que os ponteiros sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="2a9a4-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="2a9a4-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="2a9a4-116">Category</span></span>

<span data-ttu-id="2a9a4-117">Criptografia</span><span class="sxs-lookup"><span data-stu-id="2a9a4-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a9a4-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2a9a4-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

#### Affected APIs

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
