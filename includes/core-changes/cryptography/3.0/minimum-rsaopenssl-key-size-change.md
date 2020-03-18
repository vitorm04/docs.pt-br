---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567957"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="a9090-101">O tamanho mínimo para a geração de chaves RSAOpenSsl aumentou</span><span class="sxs-lookup"><span data-stu-id="a9090-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="a9090-102">O tamanho mínimo para gerar novas chaves RSA no Linux aumentou de 384 bits para 512 bits.</span><span class="sxs-lookup"><span data-stu-id="a9090-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a9090-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="a9090-103">Change description</span></span>

<span data-ttu-id="a9090-104">Começando com o .NET Core 3.0, o `LegalKeySizes` tamanho mínimo de <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>chave <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>legal <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> relatado pela propriedade em instâncias RSA de , e no Linux aumentou de 384 para 512.</span><span class="sxs-lookup"><span data-stu-id="a9090-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="a9090-105">Como resultado, em .NET Core 2.2 e versões anteriores, uma chamada de método como `RSA.Create(384)` sucesso.</span><span class="sxs-lookup"><span data-stu-id="a9090-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="a9090-106">Nas versões .NET Core 3.0 `RSA.Create(384)` e posteriores, a chamada do método lança uma exceção indicando que o tamanho é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="a9090-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="a9090-107">Essa mudança foi feita porque o OpenSSL, que realiza as operações criptográficas no Linux, aumentou seu mínimo entre as versões 1.0.2 e 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="a9090-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="a9090-108">O .NET Core 3.0 prefere o OpenSSL 1.1.x a 1.0.x, e a versão mínima relatada foi levantada para refletir essa nova limitação de dependência mais alta.</span><span class="sxs-lookup"><span data-stu-id="a9090-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a9090-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a9090-109">Version introduced</span></span>

<span data-ttu-id="a9090-110">3.0</span><span class="sxs-lookup"><span data-stu-id="a9090-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a9090-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a9090-111">Recommended action</span></span>

<span data-ttu-id="a9090-112">Se você chamar qualquer uma das APIs afetadas, certifique-se de que o tamanho de qualquer tecla gerada não seja menor do que o mínimo do provedor.</span><span class="sxs-lookup"><span data-stu-id="a9090-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="a9090-113">RSA de 384 bits já é considerada insegura (assim como rsa de 512 bits).</span><span class="sxs-lookup"><span data-stu-id="a9090-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="a9090-114">Recomendações modernas, como [nist Special Publication 800-57 Part 1 Revisão 4,](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)sugerem 2048 bits como o tamanho mínimo para chaves recém-geradas.</span><span class="sxs-lookup"><span data-stu-id="a9090-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="a9090-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="a9090-115">Category</span></span>

<span data-ttu-id="a9090-116">Criptografia</span><span class="sxs-lookup"><span data-stu-id="a9090-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a9090-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a9090-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
