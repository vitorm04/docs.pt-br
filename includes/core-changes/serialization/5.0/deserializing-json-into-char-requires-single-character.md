---
ms.openlocfilehash: 8209c5336983bde13a698fbc68e6a099091071f7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844494"
---
### <a name="jsonserializerdeserialize-requires-single-character-string"></a><span data-ttu-id="65bdf-101">JsonSerializer. Desserialize requer cadeia de caracteres de caractere único</span><span class="sxs-lookup"><span data-stu-id="65bdf-101">JsonSerializer.Deserialize requires single-character string</span></span>

<span data-ttu-id="65bdf-102">Quando o parâmetro de tipo é <xref:System.Char> , o argumento de cadeia de caracteres <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> deve conter um único caractere para que a desserialização tenha sucesso.</span><span class="sxs-lookup"><span data-stu-id="65bdf-102">When the type parameter is <xref:System.Char>, the string argument to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> must contain a single character for deserialization to succeed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="65bdf-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="65bdf-103">Change description</span></span>

<span data-ttu-id="65bdf-104">Nas versões anteriores do .NET, se você passar uma cadeia de caracteres com vários caracteres para <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> e o parâmetro de tipo for <xref:System.Char> , a desserialização terá êxito e apenas o primeiro caractere será desserializado.</span><span class="sxs-lookup"><span data-stu-id="65bdf-104">In previous .NET versions, if you pass a multi-character string to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> and the type parameter is <xref:System.Char>, the deserialization succeeds and only the first character is deserialized.</span></span>

<span data-ttu-id="65bdf-105">No .NET 5,0 e posterior, quando o parâmetro de tipo é <xref:System.Char> , a passagem de algo diferente de uma cadeia de caracteres de caractere único faz com que um seja <xref:System.Text.Json.JsonException> gerado.</span><span class="sxs-lookup"><span data-stu-id="65bdf-105">In .NET 5.0 and later, when the type parameter is <xref:System.Char>, passing anything other than a single-character string causes a <xref:System.Text.Json.JsonException> to be thrown.</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

#### <a name="version-introduced"></a><span data-ttu-id="65bdf-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="65bdf-106">Version introduced</span></span>

<span data-ttu-id="65bdf-107">5.0</span><span class="sxs-lookup"><span data-stu-id="65bdf-107">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="65bdf-108">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="65bdf-108">Reason for change</span></span>

<span data-ttu-id="65bdf-109"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> analisa o texto que representa um único valor JSON em uma instância do tipo especificado pelo parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="65bdf-109"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> parses text that represents a single JSON value into an instance of the type specified by the generic type parameter.</span></span> <span data-ttu-id="65bdf-110">A análise só terá sucesso quando a carga fornecida for válida para o parâmetro de tipo genérico especificado.</span><span class="sxs-lookup"><span data-stu-id="65bdf-110">Parsing should only succeed when the provided payload is valid for the specified generic type parameter.</span></span> <span data-ttu-id="65bdf-111">Para um <xref:System.Char> tipo de valor, uma carga válida é uma cadeia de caracteres única.</span><span class="sxs-lookup"><span data-stu-id="65bdf-111">For a <xref:System.Char> value type, a valid payload is a single character string.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="65bdf-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="65bdf-112">Recommended action</span></span>

<span data-ttu-id="65bdf-113">Ao analisar uma cadeia de caracteres em um <xref:System.Char> tipo usando <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> , verifique se a cadeia de caracteres consiste em um único caractere.</span><span class="sxs-lookup"><span data-stu-id="65bdf-113">When parsing a string into a <xref:System.Char> type using <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>, make sure the string consists of a single character.</span></span>

#### <a name="category"></a><span data-ttu-id="65bdf-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="65bdf-114">Category</span></span>

<span data-ttu-id="65bdf-115">Serialização</span><span class="sxs-lookup"><span data-stu-id="65bdf-115">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="65bdf-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="65bdf-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

-->
