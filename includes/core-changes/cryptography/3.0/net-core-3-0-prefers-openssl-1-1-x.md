---
ms.openlocfilehash: 65d8ca480d41a3807473583355fe8be41e0e9701
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274826"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3.0 prefere OpenSSL 1.1.x ao OpenSSL 1.0.x

O .NET Core for Linux, que funciona em várias distribuições Linux, pode suportar tanto o OpenSSL 1.0.x quanto o OpenSSL 1.1.x.  .NET Core 2.1 e .NET Core 2.2 olham para 1.0.x primeiro, depois recuam para 1.1.x; .NET Core 3.0 parece 1.1.x primeiro. Essa mudança foi feita para adicionar suporte a novos padrões criptográficos.

Essa alteração pode impactar bibliotecas ou aplicativos que fazem interop de plataforma com os tipos de interop específicos do OpenSSL no .NET Core.

#### <a name="change-description"></a>Descrição da alteração

No .NET Core 2.2 e nas versões anteriores, o tempo de execução prefere carregar openssl 1.0.x sobre 1.1.x. Isso significa <xref:System.IntPtr> que <xref:System.Runtime.InteropServices.SafeHandle> os e os tipos para interop com OpenSSL são usados com libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 por preferência.

A partir do .NET Core 3.0, o tempo de execução prefere carregar openssl 1.1.x sobre OpenSSL 1.0.x, de modo que os <xref:System.IntPtr> e <xref:System.Runtime.InteropServices.SafeHandle> tipos para interop com OpenSSL são usados com libcrypto.so.1 / libcrypto.so.11 / libcrypto.so.1.1.1 / libcrypto.so.1 / libcrypto.so.1 por preferência. Como resultado, bibliotecas e aplicativos que interoperam diretamente com o OpenSSL podem ter ponteiros incompatíveis com os valores expostos ao núcleo .NET ao atualizar do .NET Core 2.1 ou .NET Core 2.2.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Bibliotecas e aplicativos que fazem operações diretas com o OpenSSL precisam ter cuidado para garantir que estejam usando a mesma versão do OpenSSL que o tempo de execução do .NET Core.

Todas as bibliotecas ou <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> aplicativos que usam ou valorizam os tipos criptográficos .NET Core diretamente com <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> o OpenSSL devem comparar a versão da biblioteca que eles usam com a nova propriedade para garantir que os ponteiros sejam compatíveis.

#### <a name="category"></a>Categoria

Criptografia

#### <a name="affected-apis"></a>APIs afetadas

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
