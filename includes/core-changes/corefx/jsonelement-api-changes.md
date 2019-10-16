---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237284"
---
### <a name="jsonelement-api-changes"></a>Alterações da API jsonelement

A partir do .NET Core 3,0 Preview 7, algumas APIs <xref:System.Text.Json.JsonElement> foram alteradas para permitir uma descoberta mais fácil e maior usabilidade.

#### <a name="change-description"></a>Alterar descrição

No .NET Core 3,0 Preview 7, as APIs <xref:System.Text.Json.JsonElement> foram alteradas da seguinte maneira para permitir uma descoberta mais fácil e maior usabilidade.

1. Todas as sobrecargas de método `WriteProperty` foram removidas do <xref:System.Text.Json.JsonElement>. Isso afeta o código como o seguinte:

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

1. `WriteValue` foi renomeado como <xref:System.Text.Json.JsonElement.WriteTo%2A>. Isso afeta o código como o seguinte:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A> agora gera um <xref:System.ArgumentNullException> quando seu parâmetro de método é `null`.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 7

#### <a name="recommended-action"></a>Ação recomendada

Se o seu código for afetado por essas alterações, você poderá fazer o seguinte:

- Não há API de substituição para as sobrecargas `WriteProperty` em <xref:System.Text.Json.JsonElement>. Em vez disso, você pode chamar uma das sobrecargas <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> junto com o método <xref:System.Text.Json.JsonElement.WriteTo%2A> para atingir o mesmo resultado. Por exemplo:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Renomeie o método `WriteValue` como <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>. O parâmetro do método permanece inalterado. Por exemplo, o código anterior deve ser alterado para o seguinte:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Manipule o <xref:System.ArgumentNullException> em chamadas para o método <xref:System.Text.Json.JsonElement.WriteTo%2A>.

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
