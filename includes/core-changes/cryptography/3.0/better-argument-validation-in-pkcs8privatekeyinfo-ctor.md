---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449200"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Melhor validação de argumentos no construtor Pkcs8PrivateKeyInfo

Começando com a visualização .NET `Pkcs8PrivateKeyInfo` Core 3.0 `algorithmParameters` 9, o construtor valida o parâmetro como um único valor codificado por BER.

#### <a name="change-description"></a>Descrição da alteração

Antes do .NET Core 3.0 Preview 9, `algorithmParameters` o [ `Pkcs8PrivateKeyInfo` construtor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) não validou o argumento.  Quando este argumento representava um valor inválido, o construtor teria <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>sucesso, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>mas <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> uma chamada para <xref:System.ArgumentException> qualquer um dos <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>métodos, <xref:System.Security.Cryptography.CryptographicException>ou métodos jogaria ma ou um argumento que eles não aceitassem (`preEncodedValue`) ou um .

Se for executado com o .NET Core 3.0 antes da <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> visualização 9, o código a seguir será executado apenas quando o método for chamado:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

A partir do .NET Core 3.0 Preview 9, o argumento é validado na <xref:System.Security.Cryptography.CryptographicException>construtora, e um valor inválido resulta no método de lançamento de um . Essa alteração move a exceção mais perto da fonte do erro de dados. Por exemplo: 

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 9

#### <a name="recommended-action"></a>Ação recomendada

Certifique-se `algorithmParameters` de que apenas valores válidos são fornecidos ou que chamadas para o `Pkcs8PrivateKeyInfo` teste de construtor para ambos <xref:System.ArgumentException> e <xref:System.Security.Cryptography.CryptographicException> se o manuseio de exceção for desejado.

### <a name="category"></a>Categoria

Criptografia

### <a name="affected-apis"></a>APIs afetadas

- [Construtor pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
