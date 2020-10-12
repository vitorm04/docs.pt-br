---
ms.openlocfilehash: 5b49dcae45e44bfd9ec3e150ad25c3f21d62c18e
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955325"
---
### <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a>JsonSerializer. Serialize gera ArgumentNullException quando o parâmetro de tipo é nulo

<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType><xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> as sobrecargas que têm um <xref:System.Type> parâmetro agora lançam um <xref:System.ArgumentNullException> sempre `null` é passado para o <xref:System.Type> parâmetro.

#### <a name="change-description"></a>Descrição das alterações

No .NET Core 3,1, as <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> sobrecargas que têm um <xref:System.Type> parâmetro geram um <xref:System.ArgumentNullException> quando `null` é passado para o `Type inputType` parâmetro, mas não se o `Object value` parâmetro também for `null` . A partir do .NET 5,0, esses métodos *sempre* lançam um <xref:System.ArgumentNullException> quando `null` é passado para o <xref:System.Type> parâmetro.

Comportamento no .NET Core 3,1:

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

Comportamento no .NET 5,0 e posterior:

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

#### <a name="version-introduced"></a>Versão introduzida

5.0

#### <a name="reason-for-change"></a>Motivo da alteração

A passagem `null` para o `Type inputType` parâmetro é inaceitável e sempre deve lançar um <xref:System.ArgumentNullException> .

#### <a name="recommended-action"></a>Ação recomendada

Certifique-se de que você não está passando `null` para o `Type inputType` parâmetro desses métodos.

#### <a name="category"></a>Categoria

Serialização

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

-->
