---
ms.openlocfilehash: 375a6f57a867c2a11fe95753c1085d6d708db2bd
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237283"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="95d1f-101">Os métodos JsonEncodedText. Encode têm um argumento JavaScriptEncoder adicional</span><span class="sxs-lookup"><span data-stu-id="95d1f-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="95d1f-102">A partir do .NET Core 3,0 Preview 8, os métodos <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> contêm um argumento <xref:System.Text.Encodings.Web.JavaScriptEncoder> opcional.</span><span class="sxs-lookup"><span data-stu-id="95d1f-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="95d1f-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="95d1f-103">Change description</span></span>

<span data-ttu-id="95d1f-104">O .NET Core 3,0 inclui um novo tipo, xref: System. Text. JSON. JsonEncodedText. Encode% 2A? displayproperty = nameWithType >.</span><span class="sxs-lookup"><span data-stu-id="95d1f-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95d1f-105">A partir do .NET Core 3,0 Preview 8, a assinatura de todas as sobrecargas do método <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> foi alterada para incluir um parâmetro opcional <xref:System.Text.Encodings.Web.JavaScriptEncoder>.</span><span class="sxs-lookup"><span data-stu-id="95d1f-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="95d1f-106">Essa alteração foi feita para permitir um codificador diferente ou personalizado.</span><span class="sxs-lookup"><span data-stu-id="95d1f-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="95d1f-107">A assinatura dos métodos `Encode` no .NET Core 3,0 Preview 7 é:</span><span class="sxs-lookup"><span data-stu-id="95d1f-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="95d1f-108">A assinatura dos mesmos métodos `Encode` no .NET Core 3,0 Preview 8 e versões posteriores é:</span><span class="sxs-lookup"><span data-stu-id="95d1f-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="95d1f-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="95d1f-109">Version introduced</span></span>

<span data-ttu-id="95d1f-110">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="95d1f-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="95d1f-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="95d1f-111">Recommended action</span></span>

<span data-ttu-id="95d1f-112">Esta é apenas uma alteração de quebra binária; uma recompilação no .NET Core 3,0 Preview 8 ou uma versão posterior corrigirá quaisquer problemas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="95d1f-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="95d1f-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="95d1f-113">Category</span></span>

<span data-ttu-id="95d1f-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="95d1f-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="95d1f-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="95d1f-115">Affected APIs</span></span>

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
