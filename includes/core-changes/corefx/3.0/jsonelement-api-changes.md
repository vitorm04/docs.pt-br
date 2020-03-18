---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568090"
---
### <a name="jsonelement-api-changes"></a>Mudanças na API do JsonElement

Começando com o .NET Core 3.0 Preview 7, algumas APIs foram alteradas <xref:System.Text.Json.JsonElement> para permitir uma descoberta mais fácil e maior usabilidade.

#### <a name="change-description"></a>Descrição da alteração

No .NET Core 3.0 <xref:System.Text.Json.JsonElement> Preview 7, as APIs mudaram da seguinte forma para permitir uma descoberta mais fácil e maior usabilidade.

1. Todas `WriteProperty` as sobrecargas <xref:System.Text.Json.JsonElement>do método foram removidas de . Isso afeta o código, como o seguinte:

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

1. `WriteValue`foi renomeado <xref:System.Text.Json.JsonElement.WriteTo%2A>como . Isso afeta o código, como o seguinte:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>agora lança <xref:System.ArgumentNullException> um quando seu `null`parâmetro de método é .

#### <a name="version-introduced"></a>Versão introduzida

3.0 Pré-visualização 7

#### <a name="recommended-action"></a>Ação recomendada

Se o seu código for afetado por essas alterações, você poderá fazer o seguinte:

- Não há API de `WriteProperty` substituição <xref:System.Text.Json.JsonElement>para as sobrecargas em . Em vez disso, você <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> pode chamar <xref:System.Text.Json.JsonElement.WriteTo%2A> uma das sobrecargas junto com o método para alcançar o mesmo resultado. Por exemplo: 

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Renomeie `WriteValue` <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>o método para . O parâmetro do método permanece inalterado. Por exemplo, o código anterior deve ser alterado para o seguinte:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Manuseie <xref:System.ArgumentNullException> as <xref:System.Text.Json.JsonElement.WriteTo%2A> chamadas para o método.

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
