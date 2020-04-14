---
ms.openlocfilehash: b5b724afefcce69df706f2bea0b1612db653af03
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274941"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="858b1-101">O tamanho mínimo para a geração de chaves RSAOpenSsl aumentou</span><span class="sxs-lookup"><span data-stu-id="858b1-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="858b1-102">O tamanho mínimo para gerar novas chaves RSA no Linux aumentou de 384 bits para 512 bits.</span><span class="sxs-lookup"><span data-stu-id="858b1-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="858b1-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="858b1-103">Change description</span></span>

<span data-ttu-id="858b1-104">Começando com o .NET Core 3.0, o `LegalKeySizes` tamanho mínimo de <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>chave <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>legal <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> relatado pela propriedade em instâncias RSA de , e no Linux aumentou de 384 para 512.</span><span class="sxs-lookup"><span data-stu-id="858b1-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="858b1-105">Como resultado, em .NET Core 2.2 e versões anteriores, uma chamada de método como `RSA.Create(384)` sucesso.</span><span class="sxs-lookup"><span data-stu-id="858b1-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="858b1-106">Nas versões .NET Core 3.0 `RSA.Create(384)` e posteriores, a chamada do método lança uma exceção indicando que o tamanho é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="858b1-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="858b1-107">Essa mudança foi feita porque o OpenSSL, que realiza as operações criptográficas no Linux, aumentou seu mínimo entre as versões 1.0.2 e 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="858b1-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="858b1-108">O .NET Core 3.0 prefere o OpenSSL 1.1.x a 1.0.x, e a versão mínima relatada foi levantada para refletir essa nova limitação de dependência mais alta.</span><span class="sxs-lookup"><span data-stu-id="858b1-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="858b1-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="858b1-109">Version introduced</span></span>

<span data-ttu-id="858b1-110">3.0</span><span class="sxs-lookup"><span data-stu-id="858b1-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="858b1-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="858b1-111">Recommended action</span></span>

<span data-ttu-id="858b1-112">Se você chamar qualquer uma das APIs afetadas, certifique-se de que o tamanho de qualquer tecla gerada não seja menor do que o mínimo do provedor.</span><span class="sxs-lookup"><span data-stu-id="858b1-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="858b1-113">RSA de 384 bits já é considerada insegura (assim como rsa de 512 bits).</span><span class="sxs-lookup"><span data-stu-id="858b1-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="858b1-114">Recomendações modernas, como [nist Special Publication 800-57 Part 1 Revisão 4,](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)sugerem 2048 bits como o tamanho mínimo para chaves recém-geradas.</span><span class="sxs-lookup"><span data-stu-id="858b1-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="858b1-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="858b1-115">Category</span></span>

<span data-ttu-id="858b1-116">Criptografia</span><span class="sxs-lookup"><span data-stu-id="858b1-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="858b1-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="858b1-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
