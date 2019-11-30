---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567976"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Melhor validação de argumento no Construtor Pkcs8PrivateKeyInfo

A partir do .NET Core 3,0 Preview 9, o construtor de `Pkcs8PrivateKeyInfo` valida o parâmetro `algorithmParameters` como um único valor codificado por BER.

#### <a name="change-description"></a>Alterar descrição

Antes do .NET Core 3,0 Preview 9, o [Construtor de`Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) não validou o argumento `algorithmParameters`.  Quando esse argumento representasse um valor inválido, o Construtor teria sucesso, mas uma chamada para qualquer um dos métodos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>ou <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> geraria um <xref:System.ArgumentException> para um argumento que ele não aceitou (`preEncodedValue`) ou um <xref:System.Security.Cryptography.CryptographicException>.

Se executado com o .NET Core 3,0 antes da versão prévia 9, o código a seguir lançará uma exceção somente quando o método <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> for chamado:

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

Certifique-se de que apenas valores de `algorithmParameters` válidos sejam fornecidos ou que chamem para o teste de Construtor `Pkcs8PrivateKeyInfo` para <xref:System.ArgumentException> e <xref:System.Security.Cryptography.CryptographicException> se o tratamento de exceção for desejado.

### <a name="category"></a>Categoria

Criptografia

### <a name="affected-apis"></a>APIs afetadas

- [Construtor Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
