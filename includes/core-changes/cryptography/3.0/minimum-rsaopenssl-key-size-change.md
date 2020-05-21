---
ms.openlocfilehash: 3d94023fc508a56304587121c6cf1444c87b0d52
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721637"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="ae30b-101">O tamanho mínimo para geração de chave RSAOpenSsl aumentou</span><span class="sxs-lookup"><span data-stu-id="ae30b-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="ae30b-102">O tamanho mínimo para gerar novas chaves RSA no Linux aumentou de 384 bits para 512 bits.</span><span class="sxs-lookup"><span data-stu-id="ae30b-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ae30b-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="ae30b-103">Change description</span></span>

<span data-ttu-id="ae30b-104">A partir do .NET Core 3,0, o tamanho mínimo da chave legal relatado pela `LegalKeySizes` Propriedade nas instâncias RSA de <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> , <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A> e <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> no Linux aumentou de 384 para 512.</span><span class="sxs-lookup"><span data-stu-id="ae30b-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="ae30b-105">Como resultado, no .NET Core 2,2 e em versões anteriores, uma chamada de método como o é `RSA.Create(384)` bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="ae30b-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="ae30b-106">No .NET Core 3,0 e versões posteriores, a chamada do método `RSA.Create(384)` gera uma exceção indicando que o tamanho é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="ae30b-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="ae30b-107">Essa alteração foi feita porque o OpenSSL, que executa as operações criptográficas no Linux, aumentou seu mínimo entre as versões 1.0.2 e 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="ae30b-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="ae30b-108">O .NET Core 3,0 prefere o OpenSSL 1.1. x a 1,0. x e a versão relatada mínima foi gerada para refletir essa nova limitação de dependência mais alta.</span><span class="sxs-lookup"><span data-stu-id="ae30b-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ae30b-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ae30b-109">Version introduced</span></span>

<span data-ttu-id="ae30b-110">3.0</span><span class="sxs-lookup"><span data-stu-id="ae30b-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ae30b-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ae30b-111">Recommended action</span></span>

<span data-ttu-id="ae30b-112">Se você chamar qualquer uma das APIs afetadas, certifique-se de que o tamanho de qualquer chave gerada não seja menor do que o mínimo do provedor.</span><span class="sxs-lookup"><span data-stu-id="ae30b-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="ae30b-113">o RSA de 384 bits já é considerado inseguro (como é o RSA de 512 bits).</span><span class="sxs-lookup"><span data-stu-id="ae30b-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="ae30b-114">As recomendações modernas, como a [publicação especial do NIST 800-57 parte 1 revisão 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), sugerem 2048 bits como o tamanho mínimo para chaves geradas recentemente.</span><span class="sxs-lookup"><span data-stu-id="ae30b-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="ae30b-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="ae30b-115">Category</span></span>

<span data-ttu-id="ae30b-116">Criptografia</span><span class="sxs-lookup"><span data-stu-id="ae30b-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ae30b-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ae30b-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
#### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
