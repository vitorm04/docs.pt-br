---
ms.openlocfilehash: b965c3a975b0f2cadd906799fef1665261d96d6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182014"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms usa como padrão a criptografia AES-256

O algoritmo de criptografia simétrica padrão usado `EnvelopedCms` pelo foi alterado de TripleDES para AES-256.

#### <a name="details"></a>Detalhes

No .NET Core Preview 7 e em versões anteriores, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> quando é usado para criptografar dados sem especificar um algoritmo de criptografia simétrica por meio de uma sobrecarga de construtor, os dados foram criptografados com o algoritmo TripleDES/3DES/3DEA/DES3-Ede.

A partir do .NET Core 3,0 Preview 8 (por meio da versão 4.6.0 do pacote NuGet [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ), o algoritmo padrão foi alterado para AES-256 para modernização do algoritmo e para melhorar a segurança das opções padrão. Se um certificado de destinatário de mensagem tiver uma chave pública Diffie-Hellman (não-EC), a operação de criptografia poderá <xref:System.Security.Cryptography.CryptographicException> falhar com um devido a limitações na plataforma subjacente.

No código de exemplo a seguir, os dados são criptografados com TripleDES se executados no .NET Core 3,0 Preview 7 ou anterior. Se estiver executando no .NET Core 3,0 Preview 8 ou posterior, ele será criptografado com AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 8

#### <a name="recommended-action"></a>Ação recomendada

Se você for afetado negativamente pela alteração, poderá restaurar a criptografia TripleDES especificando explicitamente o identificador do algoritmo de criptografia em um <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> Construtor que inclua um parâmetro do tipo <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, como:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Categoria

Criptografia

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
