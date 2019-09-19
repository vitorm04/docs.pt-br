---
ms.openlocfilehash: 07ab65de16b72bd0844a39e4b35235c5f043f3ec
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117183"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>O tamanho mínimo para geração de chave RSAOpenSsl aumentou

O tamanho mínimo para gerar novas chaves RSA no Linux aumentou de 384 bits para 512 bits.

#### <a name="change-description"></a>Alterar descrição

A partir do .NET Core 3,0, o tamanho mínimo da chave legal relatada pela `LegalKeySizes` Propriedade em instâncias RSA de < System. Security. Cryptography. RSA. Create% 2a? TipoDeExibição = nameWithType >, < System. Security. Cryptography. RSAOpenSsl.% 23ctor% 2A? displayproperty = nameWithType > e < System. Security. Cryptography. RSACryptoServicePlatform.% 23ctor% 2A? displayproperty = nameWithType > no Linux aumentou de 384 para 512.

Como resultado, no .NET Core 2,2 e em versões anteriores, uma chamada de método como `RSA.Create(384)` o é bem sucedido. No .NET Core 3,0 e versões posteriores, a chamada `RSA.Create(384)` do método gera uma exceção indicando que o tamanho é muito pequeno.

Essas alterações foram feitas porque o OpenSSL, que executa as operações criptográficas no Linux, aumentou seu mínimo entre as versões 1.0.2 e 1.1.0.  O .NET Core 3,0 prefere o OpenSSL 1.1. x a 1,0. x e a versão relatada mínima foi gerada para refletir essa nova limitação de dependência mais alta.

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
