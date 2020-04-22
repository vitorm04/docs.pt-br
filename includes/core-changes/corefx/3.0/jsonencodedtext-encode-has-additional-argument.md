---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021578"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>Os métodos JsonEncodedText.Encode têm um argumento adicional do JavaScriptEncoder

A partir do .NET Core 3.0 Preview 8, os <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> métodos contêm um argumento opcional. <xref:System.Text.Encodings.Web.JavaScriptEncoder>

#### <a name="change-description"></a>Descrição da alteração

.NET Core 3.0 inclui um novo tipo, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>. Começando com .NET Core 3.0 Preview <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 8, a assinatura de <xref:System.Text.Encodings.Web.JavaScriptEncoder> todas as sobrecargas do método foi alterada para incluir um parâmetro opcional. Esta alteração foi feita para permitir um codificador diferente ou personalizado.

A assinatura `Encode` dos métodos no .NET Core 3.0 Preview 7 é:

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value);
        public static JsonEncodedText Encode(string value);
    }
}
```

A assinatura dos `Encode` mesmos métodos nas versões .NET Core 3.0 Preview 8 e posteriores é:

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(string value, JavaScriptEncoder encoder = null);
    }
}
```

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3.0 Visualização 8

#### <a name="recommended-action"></a>Ação recomendada

Esta é apenas uma mudança binária de quebra; uma recompilação contra o .NET Core 3.0 Preview 8 ou uma versão posterior corrigirá quaisquer problemas de tempo de execução.

#### <a name="category"></a>Categoria

Bibliotecas Core .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
