---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216331"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>O tamanho mínimo para geração de chave RSAOpenSsl aumentou

O tamanho mínimo para gerar novas chaves RSA no Linux aumentou de 384 bits para 512 bits.

#### <a name="change-description"></a>Alterar descrição

A partir do .NET Core 3,0, o tamanho mínimo da chave legal relatado `LegalKeySizes` pela propriedade nas instâncias RSA <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>de <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, e <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> no Linux aumentou de 384 para 512.

Como resultado, no .NET Core 2,2 e em versões anteriores, uma chamada de método como `RSA.Create(384)` o é bem sucedido. No .NET Core 3,0 e versões posteriores, a chamada `RSA.Create(384)` do método gera uma exceção indicando que o tamanho é muito pequeno.

Essa alteração foi feita porque o OpenSSL, que executa as operações criptográficas no Linux, aumentou seu mínimo entre as versões 1.0.2 e 1.1.0. O .NET Core 3,0 prefere o OpenSSL 1.1. x a 1,0. x e a versão relatada mínima foi gerada para refletir essa nova limitação de dependência mais alta.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Se você chamar qualquer uma das APIs afetadas, certifique-se de que o tamanho de qualquer chave gerada não seja menor do que o mínimo do provedor.

> [!NOTE]
> o RSA de 384 bits já é considerado inseguro (como é o RSA de 512 bits). As recomendações modernas, como a [publicação especial do NIST 800-57 parte 1 revisão 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), sugerem 2048 bits como o tamanho mínimo para chaves geradas recentemente.

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
