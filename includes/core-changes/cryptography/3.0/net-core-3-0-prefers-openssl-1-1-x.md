---
ms.openlocfilehash: b49b2f88b130bb952b77964d5bf38374dc606385
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567962"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>O .NET Core 3,0 prefere o OpenSSL 1.1. x ao OpenSSL 1.0. x

O .NET Core para Linux, que funciona em várias distribuições do Linux, pode dar suporte a OpenSSL 1.0. x e OpenSSL 1.1. x.  .NET Core 2,1 e .NET Core 2,2 Procure 1,0. x primeiro e, em seguida, retorne para 1.1. x; o .NET Core 3,0 procura por 1,1. x primeiro. Essa alteração foi feita para adicionar suporte para novos padrões de criptografia.

Essa alteração pode afetar as bibliotecas ou os aplicativos que fazem a interoperabilidade de plataforma com os tipos de interoperabilidade específicos do OpenSSL no .NET Core.

#### <a name="change-description"></a>Alterar descrição

No .NET Core 2,2 e versões anteriores, o tempo de execução prefere carregar o OpenSSL 1.0. x acima de 1.1. x. Isso significa que os tipos de <xref:System.IntPtr> e <xref:System.Runtime.InteropServices.SafeHandle> para interoperabilidade com OpenSSL são usados com libcrypto. por isso, 1.0.0/libcrypto. portanto. 1.0/libcrypto. portanto, 10 por preferência.

A partir do .NET Core 3,0, o tempo de execução prefere carregar o OpenSSL 1.1. x em relação ao OpenSSL 1.0. x, de modo que os tipos <xref:System.IntPtr> e <xref:System.Runtime.InteropServices.SafeHandle> para interoperabilidade com OpenSSL são usados com libcrypto. portanto. 1.1/libcrypto. portanto, 11/libcrypto. portanto, 1.1.0/libcrypto. portanto, 1.1.1 por preferência. Como resultado, as bibliotecas e os aplicativos que interoperam com o OpenSSL diretamente podem ter ponteiros incompatíveis com os valores expostos do .NET Core ao atualizar do .NET Core 2,1 ou do .NET Core 2,2.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Bibliotecas e aplicativos que fazem operações diretas com o OpenSSL precisam ter cuidado para garantir que estejam usando a mesma versão do OpenSSL que o tempo de execução do .NET Core.

Todas as bibliotecas ou aplicativos que usam <xref:System.IntPtr> ou <xref:System.Runtime.InteropServices.SafeHandle> valores dos tipos de criptografia do .NET Core diretamente com o OpenSSL devem comparar a versão da biblioteca que usam com a nova propriedade <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> para garantir que os ponteiros sejam compatíveis.

#### <a name="category"></a>Categoria

Criptografia

#### <a name="affected-apis"></a>APIs afetadas

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
