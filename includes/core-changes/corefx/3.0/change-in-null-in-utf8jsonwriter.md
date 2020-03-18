---
ms.openlocfilehash: 7c39fe7ffd59fa7a5564bb45f32a6a2fbe0ddb33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568132"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="ead02-101">Mudança na semântica de `(string)null` em Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="ead02-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="ead02-102">Em .NET Core 3.0 Visualização 7, a seqüência nula é tratada como a seqüência vazia em <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="ead02-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="ead02-103">Começando com .NET Core 3.0 Preview 8, a seqüência de nulidade lança uma exceção quando usada como nome de propriedade, e emite o token nulo JSON quando usado como um valor.</span><span class="sxs-lookup"><span data-stu-id="ead02-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ead02-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="ead02-104">Change description</span></span>

<span data-ttu-id="ead02-105">No .NET Core 3.0 `null` Preview 7, `""` a seqüência foi tratada tanto como ao escrever nomes de propriedade quanto ao escrever valores.</span><span class="sxs-lookup"><span data-stu-id="ead02-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="ead02-106">Começando com .NET Core 3.0 `null` Preview 8, um `null` nome de propriedade <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> lança <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>um `ArgumentNullException`, e um valor é tratado como uma chamada para ou .</span><span class="sxs-lookup"><span data-stu-id="ead02-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ead02-107">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ead02-107">Consider the following code:</span></span>

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

<span data-ttu-id="ead02-108">Se for executado com .NET Core 3.0 Preview 7, o escritor produzirá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="ead02-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="ead02-109">Começando com .NET Core 3.0 Preview `writer.WriteString(propertyName1, propertyValue1)` 8, a chamada para lançar um <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="ead02-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="ead02-110">Se `propertyName1 = null` for substituída `propertyName1 = string.Empty`por , a saída seria agora:</span><span class="sxs-lookup"><span data-stu-id="ead02-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="ead02-111">Essa mudança foi feita para melhor `null` alinhar com as expectativas dos chamadores para os valores.</span><span class="sxs-lookup"><span data-stu-id="ead02-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ead02-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ead02-112">Version introduced</span></span>

<span data-ttu-id="ead02-113">3.0 Visualização 8</span><span class="sxs-lookup"><span data-stu-id="ead02-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ead02-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ead02-114">Recommended action</span></span>

<span data-ttu-id="ead02-115">Ao escrever nomes e <xref:System.Text.Json.Utf8JsonWriter> valores de propriedades com a classe:</span><span class="sxs-lookup"><span data-stu-id="ead02-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="ead02-116">Certifique-se`null` de que as não-strings são usadas como nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="ead02-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="ead02-117">Se o comportamento anterior for desejado, use uma invocação de coalizão nula; por exemplo, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span><span class="sxs-lookup"><span data-stu-id="ead02-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="ead02-118">Se escrever `null` um `null` literal para um valor de corda não for desejável, use uma invocação de coalescência nula; por exemplo, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span><span class="sxs-lookup"><span data-stu-id="ead02-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="ead02-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="ead02-119">Category</span></span>

<span data-ttu-id="ead02-120">CoreFx</span><span class="sxs-lookup"><span data-stu-id="ead02-120">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ead02-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ead02-121">Affected APIs</span></span>

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
