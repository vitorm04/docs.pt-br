---
ms.openlocfilehash: f72a9f60d0adcace2df6f1761940f8d8cd33d3af
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119285"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Melhor validação de argumento no Construtor Pkcs8PrivateKeyInfo

A partir do .NET Core 3,0 Preview 9, `Pkcs8PrivateKeyInfo` o Construtor valida o `algorithmParameters` parâmetro como um único valor codificado pelo ber. 

#### <a name="change-description"></a>Alterar descrição

Antes do .NET Core 3,0 Preview 9, o [ `Pkcs8PrivateKeyInfo` Construtor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) não validou `algorithmParameters` o argumento.  Quando esse argumento representasse um valor inválido, o Construtor teria sucesso, mas uma chamada para qualquer um <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>dos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>métodos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> ou geraria um <xref:System.ArgumentException> para um argumento que não aceitou (`preEncodedValue`) ou um <xref:System.Security.Cryptography.CryptographicException>.

Se executado com o .NET Core 3,0 antes da versão prévia 9, o código a seguir lançará <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> uma exceção somente quando o método for chamado:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

A partir do .NET Core 3,0 Preview 9, o argumento é validado no construtor e um valor inválido resulta no método que gera um <xref:System.Security.Cryptography.CryptographicException>. Essa alteração move a exceção mais perto da origem do erro de dados. Por exemplo:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Certifique-se de `algorithmParameters` que apenas valores válidos sejam fornecidos ou que chame `Pkcs8PrivateKeyInfo` para o teste de <xref:System.ArgumentException> Construtor <xref:System.Security.Cryptography.CryptographicException> para ambos e se a manipulação de exceção for desejada.

### <a name="category"></a>Categoria

Criptografia

### <a name="affected-apis"></a>APIs afetadas

- [Construtor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->