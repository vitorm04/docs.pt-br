---
ms.openlocfilehash: c9547cdc2f127cf13a3610118a26736930fcd8bd
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021638"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a>Mudança na semântica de `(string)null` em Utf8JsonWriter

Em .NET Core 3.0 Visualização 7, a seqüência nula é tratada como a seqüência vazia em <xref:System.Text.Json.Utf8JsonWriter>. Começando com .NET Core 3.0 Preview 8, a seqüência de nulidade lança uma exceção quando usada como nome de propriedade, e emite o token nulo JSON quando usado como um valor.

#### <a name="change-description"></a>Descrição da alteração

No .NET Core 3.0 `null` Preview 7, `""` a seqüência foi tratada tanto como ao escrever nomes de propriedade quanto ao escrever valores.  

Começando com .NET Core 3.0 `null` Preview 8, um `null` nome de propriedade <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> lança <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>um `ArgumentNullException`, e um valor é tratado como uma chamada para ou .

Considere o código a seguir:

```csharp
string propertyName1 = null;
string propertyValue1 = null;
string propertyName2 = "prop2";
string propertyValue2 = null;
string simpleValue1 = null;

using (Utf8JsonWriter writer = new Utf8JsonWriter(stream))
{
    writer.WriteStartArray();

    writer.WriteStartObject();
    writer.WriteString(propertyName1, propertyValue1);
    writer.WriteString(propertyName2, propertyValue2);
    writer.WriteEndObject();

    writer.WriteStringValue(simpleValue1);

    writer.WriteEndArray();
}
```

Se for executado com .NET Core 3.0 Preview 7, o escritor produzirá a seguinte saída:

```js
[{"":"","prop2":""},""]
```

Começando com .NET Core 3.0 Preview `writer.WriteString(propertyName1, propertyValue1)` 8, a chamada para lançar um <xref:System.ArgumentNullException>.  Se `propertyName1 = null` for substituída `propertyName1 = string.Empty`por , a saída seria agora:

```js
[{"":null,"prop2":null},null]
```

Essa mudança foi feita para melhor `null` alinhar com as expectativas dos chamadores para os valores.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 8

#### <a name="recommended-action"></a>Ação recomendada

Ao escrever nomes e <xref:System.Text.Json.Utf8JsonWriter> valores de propriedades com a classe:

- Certifique-se`null` de que as não-strings são usadas como nomes de propriedade.

- Se o comportamento anterior for desejado, use uma invocação de coalizão nula; por exemplo, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.

- Se escrever `null` um `null` literal para um valor de corda não for desejável, use uma invocação de coalescência nula; por exemplo, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.

#### <a name="category"></a>Categoria

Bibliotecas Core .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Char%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Char})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)`

-->
