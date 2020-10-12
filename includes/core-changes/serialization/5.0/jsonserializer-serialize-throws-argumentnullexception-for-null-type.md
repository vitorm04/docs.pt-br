---
ms.openlocfilehash: 5b49dcae45e44bfd9ec3e150ad25c3f21d62c18e
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955325"
---
### <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a><span data-ttu-id="e8afe-101">JsonSerializer. Serialize gera ArgumentNullException quando o parâmetro de tipo é nulo</span><span class="sxs-lookup"><span data-stu-id="e8afe-101">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>

<span data-ttu-id="e8afe-102"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType><xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> as sobrecargas que têm um <xref:System.Type> parâmetro agora lançam um <xref:System.ArgumentNullException> sempre `null` é passado para o <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e8afe-102"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter now throw an <xref:System.ArgumentNullException> whenever `null` is passed for the <xref:System.Type> parameter.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e8afe-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="e8afe-103">Change description</span></span>

<span data-ttu-id="e8afe-104">No .NET Core 3,1, as <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> sobrecargas que têm um <xref:System.Type> parâmetro geram um <xref:System.ArgumentNullException> quando `null` é passado para o `Type inputType` parâmetro, mas não se o `Object value` parâmetro também for `null` .</span><span class="sxs-lookup"><span data-stu-id="e8afe-104">In .NET Core 3.1, the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter throw an <xref:System.ArgumentNullException> when `null` is passed for the `Type inputType` parameter, but not if the `Object value` parameter is also `null`.</span></span> <span data-ttu-id="e8afe-105">A partir do .NET 5,0, esses métodos *sempre* lançam um <xref:System.ArgumentNullException> quando `null` é passado para o <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e8afe-105">Starting in .NET 5.0, these methods *always* throw an <xref:System.ArgumentNullException> when `null` is passed for the <xref:System.Type> parameter.</span></span>

<span data-ttu-id="e8afe-106">Comportamento no .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="e8afe-106">Behavior in .NET Core 3.1:</span></span>

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

<span data-ttu-id="e8afe-107">Comportamento no .NET 5,0 e posterior:</span><span class="sxs-lookup"><span data-stu-id="e8afe-107">Behavior in .NET 5.0 and later:</span></span>

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

#### <a name="version-introduced"></a><span data-ttu-id="e8afe-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e8afe-108">Version introduced</span></span>

<span data-ttu-id="e8afe-109">5.0</span><span class="sxs-lookup"><span data-stu-id="e8afe-109">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e8afe-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="e8afe-110">Reason for change</span></span>

<span data-ttu-id="e8afe-111">A passagem `null` para o `Type inputType` parâmetro é inaceitável e sempre deve lançar um <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="e8afe-111">Passing in `null` for the `Type inputType` parameter is unacceptable and should always throw an <xref:System.ArgumentNullException>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e8afe-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e8afe-112">Recommended action</span></span>

<span data-ttu-id="e8afe-113">Certifique-se de que você não está passando `null` para o `Type inputType` parâmetro desses métodos.</span><span class="sxs-lookup"><span data-stu-id="e8afe-113">Make sure that you are not passing `null` for the `Type inputType` parameter of these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="e8afe-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="e8afe-114">Category</span></span>

<span data-ttu-id="e8afe-115">Serialização</span><span class="sxs-lookup"><span data-stu-id="e8afe-115">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e8afe-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e8afe-116">Affected APIs</span></span>

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
