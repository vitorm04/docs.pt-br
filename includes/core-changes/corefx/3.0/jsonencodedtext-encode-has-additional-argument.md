---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021578"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="a6162-101">Os métodos JsonEncodedText.Encode têm um argumento adicional do JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="a6162-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="a6162-102">A partir do .NET Core 3.0 Preview 8, os <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> métodos contêm um argumento opcional. <xref:System.Text.Encodings.Web.JavaScriptEncoder></span><span class="sxs-lookup"><span data-stu-id="a6162-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a6162-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="a6162-103">Change description</span></span>

<span data-ttu-id="a6162-104">.NET Core 3.0 inclui um novo tipo, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6162-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a6162-105">Começando com .NET Core 3.0 Preview <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 8, a assinatura de <xref:System.Text.Encodings.Web.JavaScriptEncoder> todas as sobrecargas do método foi alterada para incluir um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="a6162-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="a6162-106">Esta alteração foi feita para permitir um codificador diferente ou personalizado.</span><span class="sxs-lookup"><span data-stu-id="a6162-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="a6162-107">A assinatura `Encode` dos métodos no .NET Core 3.0 Preview 7 é:</span><span class="sxs-lookup"><span data-stu-id="a6162-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="a6162-108">A assinatura dos `Encode` mesmos métodos nas versões .NET Core 3.0 Preview 8 e posteriores é:</span><span class="sxs-lookup"><span data-stu-id="a6162-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="a6162-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a6162-109">Version introduced</span></span>

<span data-ttu-id="a6162-110">.NET Core 3.0 Visualização 8</span><span class="sxs-lookup"><span data-stu-id="a6162-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a6162-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a6162-111">Recommended action</span></span>

<span data-ttu-id="a6162-112">Esta é apenas uma mudança binária de quebra; uma recompilação contra o .NET Core 3.0 Preview 8 ou uma versão posterior corrigirá quaisquer problemas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a6162-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="a6162-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="a6162-113">Category</span></span>

<span data-ttu-id="a6162-114">Bibliotecas Core .NET</span><span class="sxs-lookup"><span data-stu-id="a6162-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a6162-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a6162-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
