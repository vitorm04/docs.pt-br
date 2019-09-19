---
ms.openlocfilehash: 101740e828589d7d210527e3db82a1c949a6e0fd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117125"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>Os métodos JsonEncodedText. Encode têm um argumento JavaScriptEncoder adicional

A partir do .NET Core 3,0 Preview 8, <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> os métodos contêm um <xref:System.Text.Encodings.Web.JavaScriptEncoder> argumento opcional. 

#### <a name="details"></a>Detalhes

O .NET Core 3,0 inclui um novo tipo, xref: System. Text. JSON. JsonEncodedText. Encode% 2A? displayproperty = nameWithType >. A partir do .NET Core 3,0 Preview 8, a assinatura de <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> todas as sobrecargas de método foi alterada para <xref:System.Text.Encodings.Web.JavaScriptEncoder> incluir um parâmetro opcional. Essa alteração foi feita para permitir um codificador diferente ou personalizado.

A assinatura dos `Encode` métodos no .NET Core 3,0 Preview 7 é:

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

A assinatura dos mesmos `Encode` métodos no .NET Core 3,0 Preview 8 e versões posteriores é:

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

.NET Core 3,0 Preview 8

#### <a name="recommended-action"></a>Ação recomendada

Esta é apenas uma alteração de quebra binária; uma recompilação no .NET Core 3,0 Preview 8 ou uma versão posterior corrigirá quaisquer problemas de tempo de execução.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs 

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->