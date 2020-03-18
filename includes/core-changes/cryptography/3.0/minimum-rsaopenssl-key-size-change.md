---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567957"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>O tamanho mínimo para a geração de chaves RSAOpenSsl aumentou

O tamanho mínimo para gerar novas chaves RSA no Linux aumentou de 384 bits para 512 bits.

#### <a name="change-description"></a>Descrição da alteração

Começando com o .NET Core 3.0, o `LegalKeySizes` tamanho mínimo de <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>chave <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>legal <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> relatado pela propriedade em instâncias RSA de , e no Linux aumentou de 384 para 512.

Como resultado, em .NET Core 2.2 e versões anteriores, uma chamada de método como `RSA.Create(384)` sucesso. Nas versões .NET Core 3.0 `RSA.Create(384)` e posteriores, a chamada do método lança uma exceção indicando que o tamanho é muito pequeno.

Essa mudança foi feita porque o OpenSSL, que realiza as operações criptográficas no Linux, aumentou seu mínimo entre as versões 1.0.2 e 1.1.0. O .NET Core 3.0 prefere o OpenSSL 1.1.x a 1.0.x, e a versão mínima relatada foi levantada para refletir essa nova limitação de dependência mais alta.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Se você chamar qualquer uma das APIs afetadas, certifique-se de que o tamanho de qualquer tecla gerada não seja menor do que o mínimo do provedor.

> [!NOTE]
> RSA de 384 bits já é considerada insegura (assim como rsa de 512 bits). Recomendações modernas, como [nist Special Publication 800-57 Part 1 Revisão 4,](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)sugerem 2048 bits como o tamanho mínimo para chaves recém-geradas.

#### <a name="category"></a>Categoria

Criptografia

#### <a name="affected-apis"></a>APIs afetadas

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
