---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568090"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="58ea2-101">Alterações da API jsonelement</span><span class="sxs-lookup"><span data-stu-id="58ea2-101">JsonElement API changes</span></span>

<span data-ttu-id="58ea2-102">A partir do .NET Core 3,0 Preview 7, algumas APIs <xref:System.Text.Json.JsonElement> foram alteradas para permitir uma descoberta mais fácil e maior usabilidade.</span><span class="sxs-lookup"><span data-stu-id="58ea2-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="58ea2-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="58ea2-103">Change description</span></span>

<span data-ttu-id="58ea2-104">No .NET Core 3,0 Preview 7, as APIs de <xref:System.Text.Json.JsonElement> foram alteradas da seguinte maneira para permitir uma descoberta mais fácil e maior usabilidade.</span><span class="sxs-lookup"><span data-stu-id="58ea2-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="58ea2-105">Todas as sobrecargas de método de `WriteProperty` foram removidas do <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="58ea2-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="58ea2-106">Isso afeta o código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="58ea2-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="58ea2-107">`WriteValue` foi renomeado como <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="58ea2-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="58ea2-108">Isso afeta o código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="58ea2-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="58ea2-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> agora gera um <xref:System.ArgumentNullException> quando seu parâmetro de método é `null`.</span><span class="sxs-lookup"><span data-stu-id="58ea2-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="58ea2-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="58ea2-110">Version introduced</span></span>

<span data-ttu-id="58ea2-111">3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="58ea2-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="58ea2-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="58ea2-112">Recommended action</span></span>

<span data-ttu-id="58ea2-113">Se o seu código for afetado por essas alterações, você poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="58ea2-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="58ea2-114">Não há API de substituição para as sobrecargas de `WriteProperty` no <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="58ea2-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="58ea2-115">Em vez disso, você pode chamar uma das sobrecargas de <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> junto com o método <xref:System.Text.Json.JsonElement.WriteTo%2A> para obter o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="58ea2-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="58ea2-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="58ea2-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="58ea2-117">Renomeie o método `WriteValue` como <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span><span class="sxs-lookup"><span data-stu-id="58ea2-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="58ea2-118">O parâmetro do método permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="58ea2-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="58ea2-119">Por exemplo, o código anterior deve ser alterado para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="58ea2-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="58ea2-120">Manipule o <xref:System.ArgumentNullException> em chamadas para o método <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="58ea2-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="58ea2-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="58ea2-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
