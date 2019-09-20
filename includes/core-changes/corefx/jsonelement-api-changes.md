---
ms.openlocfilehash: 98893470b64de4abf7f04817871e3053bf25b86d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119299"
---
### <a name="jsonelement-api-changes"></a>Alterações da API jsonelement

A partir do .NET Core 3,0 Preview 7, <xref:System.Text.Json.JsonElement> algumas APIs foram alteradas para permitir uma descoberta mais fácil e maior usabilidade.

#### <a name="change-description"></a>Alterar descrição

No .NET Core 3,0 Preview 7, <xref:System.Text.Json.JsonElement> as APIs foram alteradas da seguinte forma para permitir uma descoberta mais fácil e maior usabilidade.

1. Todas `WriteProperty` as sobrecargas de método foram <xref:System.Text.Json.JsonElement>removidas do. Isso afeta o código como o seguinte:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
      JsonElement root = doc.RootElement;
      root.WriteProperty(propertyNameString, writer);
      // ..
      root.WriteProperty(propertyNameSpan, writer);
      // ..
      root.WriteProperty(propertyNameJsonEncoded, writer);
      // ..
      root.WriteProperty(utf8PropertyName, writer);
      //..
   }
   ```

1. `WriteValue`foi renomeado como <xref:System.Text.Json.JsonElement.WriteTo%2A>. Isso afeta o código como o seguinte:

```csharp
using (JsonDocument doc = JsonDocument.Parse(jsonString))
{
    JsonElement root = doc.RootElement;
    root.WriteValue(writer);
}

```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>Agora gera um <xref:System.ArgumentNullException> quando seu parâmetro de método `null`é.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 7

#### <a name="recommended-action"></a>Ação recomendada

Se o seu código for afetado por essas alterações, você poderá fazer o seguinte:

- Não há API de substituição para as `WriteProperty` sobrecargas no <xref:System.Text.Json.JsonElement>. Em vez disso, você pode chamar uma <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> das sobrecargas junto com <xref:System.Text.Json.JsonElement.WriteTo%2A> o método para atingir o mesmo resultado. Por exemplo:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Renomeie `WriteValue` o <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>método como. O parâmetro do método permanece inalterado. Por exemplo, o código anterior deve ser alterado para o seguinte:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Manipule o <xref:System.ArgumentNullException> em chamadas para o <xref:System.Text.Json.JsonElement.WriteTo%2A> método.

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
