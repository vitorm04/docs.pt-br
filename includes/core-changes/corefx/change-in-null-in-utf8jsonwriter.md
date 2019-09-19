---
ms.openlocfilehash: 7c39fe7ffd59fa7a5564bb45f32a6a2fbe0ddb33
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117156"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="733a3-101">Alteração na semântica de `(string)null` no Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="733a3-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="733a3-102">No .NET Core 3,0 Preview 7, a cadeia de caracteres nula é tratada como a cadeia <xref:System.Text.Json.Utf8JsonWriter>de caracteres vazia no.</span><span class="sxs-lookup"><span data-stu-id="733a3-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="733a3-103">A partir do .NET Core 3,0 Preview 8, a cadeia de caracteres nula gera uma exceção quando usada como um nome de propriedade e emite o token NULL JSON quando usado como um valor.</span><span class="sxs-lookup"><span data-stu-id="733a3-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="733a3-104">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="733a3-104">Change description</span></span>

<span data-ttu-id="733a3-105">No .NET Core 3,0 Preview 7, a `null` cadeia de caracteres foi `""` tratada como ambos ao gravar nomes de propriedade e ao gravar valores.</span><span class="sxs-lookup"><span data-stu-id="733a3-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="733a3-106">A partir do .NET Core 3,0 Preview 8, `null` um nome de propriedade `ArgumentNullException`gera um, `null` e um valor é tratado como uma <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> chamada <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>para ou.</span><span class="sxs-lookup"><span data-stu-id="733a3-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="733a3-107">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="733a3-107">Consider the following code:</span></span>

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

<span data-ttu-id="733a3-108">Se executado com o .NET Core 3,0 Preview 7, o gravador produzirá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="733a3-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="733a3-109">A partir do .NET Core 3,0 Preview 8, a chamada `writer.WriteString(propertyName1, propertyValue1)` para gera <xref:System.ArgumentNullException>um.</span><span class="sxs-lookup"><span data-stu-id="733a3-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="733a3-110">Se `propertyName1 = null` for substituído por `propertyName1 = string.Empty`, a saída agora será:</span><span class="sxs-lookup"><span data-stu-id="733a3-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="733a3-111">Essa alteração foi feita para um melhor alinhamento com as expectativas `null` do chamador para valores.</span><span class="sxs-lookup"><span data-stu-id="733a3-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="733a3-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="733a3-112">Version introduced</span></span>

<span data-ttu-id="733a3-113">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="733a3-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="733a3-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="733a3-114">Recommended action</span></span>

<span data-ttu-id="733a3-115">Ao gravar valores e nomes de propriedade com <xref:System.Text.Json.Utf8JsonWriter> a classe:</span><span class="sxs-lookup"><span data-stu-id="733a3-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="733a3-116">Verifique se não`null` há cadeias de caracteres usadas como nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="733a3-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="733a3-117">Se o comportamento anterior for desejado, use uma invocação de União nula; por exemplo, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span><span class="sxs-lookup"><span data-stu-id="733a3-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="733a3-118">Se a gravação `null` de um literal `null` para um valor de cadeia de caracteres não for desejável, use uma invocação de União `writer.WriteString(propertyName2, propertyValue2 ?? "")`nula; por exemplo,.</span><span class="sxs-lookup"><span data-stu-id="733a3-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="733a3-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="733a3-119">Category</span></span>

<span data-ttu-id="733a3-120">CoreFx</span><span class="sxs-lookup"><span data-stu-id="733a3-120">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="733a3-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="733a3-121">Affected APIs</span></span>

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
