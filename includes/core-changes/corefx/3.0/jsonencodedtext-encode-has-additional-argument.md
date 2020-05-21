---
ms.openlocfilehash: d90996ae1b87cdea815daf979bece094d8602f70
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721570"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="8c0cb-101">Os métodos JsonEncodedText. Encode têm um argumento JavaScriptEncoder adicional</span><span class="sxs-lookup"><span data-stu-id="8c0cb-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="8c0cb-102">A partir do .NET Core 3,0 Preview 8, os <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> métodos contêm um <xref:System.Text.Encodings.Web.JavaScriptEncoder> argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="8c0cb-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8c0cb-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="8c0cb-103">Change description</span></span>

<span data-ttu-id="8c0cb-104">O .NET Core 3,0 inclui um novo tipo, xref: System. Text. JSON. JsonEncodedText. Encode% 2A? displayproperty = nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c0cb-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8c0cb-105">A partir do .NET Core 3,0 Preview 8, a assinatura de todas as <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> sobrecargas de método foi alterada para incluir um <xref:System.Text.Encodings.Web.JavaScriptEncoder> parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="8c0cb-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="8c0cb-106">Essa alteração foi feita para permitir um codificador diferente ou personalizado.</span><span class="sxs-lookup"><span data-stu-id="8c0cb-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="8c0cb-107">A assinatura dos `Encode` métodos no .NET Core 3,0 Preview 7 é:</span><span class="sxs-lookup"><span data-stu-id="8c0cb-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="8c0cb-108">A assinatura dos mesmos `Encode` métodos no .NET Core 3,0 Preview 8 e versões posteriores é:</span><span class="sxs-lookup"><span data-stu-id="8c0cb-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="8c0cb-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8c0cb-109">Version introduced</span></span>

<span data-ttu-id="8c0cb-110">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="8c0cb-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8c0cb-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8c0cb-111">Recommended action</span></span>

<span data-ttu-id="8c0cb-112">Esta é apenas uma alteração de quebra binária; uma recompilação no .NET Core 3,0 Preview 8 ou uma versão posterior corrigirá quaisquer problemas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8c0cb-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="8c0cb-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="8c0cb-113">Category</span></span>

<span data-ttu-id="8c0cb-114">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="8c0cb-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c0cb-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8c0cb-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
