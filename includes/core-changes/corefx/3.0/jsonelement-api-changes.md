---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568090"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="183c6-101">Mudanças na API do JsonElement</span><span class="sxs-lookup"><span data-stu-id="183c6-101">JsonElement API changes</span></span>

<span data-ttu-id="183c6-102">Começando com o .NET Core 3.0 Preview 7, algumas APIs foram alteradas <xref:System.Text.Json.JsonElement> para permitir uma descoberta mais fácil e maior usabilidade.</span><span class="sxs-lookup"><span data-stu-id="183c6-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="183c6-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="183c6-103">Change description</span></span>

<span data-ttu-id="183c6-104">No .NET Core 3.0 <xref:System.Text.Json.JsonElement> Preview 7, as APIs mudaram da seguinte forma para permitir uma descoberta mais fácil e maior usabilidade.</span><span class="sxs-lookup"><span data-stu-id="183c6-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="183c6-105">Todas `WriteProperty` as sobrecargas <xref:System.Text.Json.JsonElement>do método foram removidas de .</span><span class="sxs-lookup"><span data-stu-id="183c6-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="183c6-106">Isso afeta o código, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="183c6-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="183c6-107">`WriteValue`foi renomeado <xref:System.Text.Json.JsonElement.WriteTo%2A>como .</span><span class="sxs-lookup"><span data-stu-id="183c6-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="183c6-108">Isso afeta o código, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="183c6-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="183c6-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>agora lança <xref:System.ArgumentNullException> um quando seu `null`parâmetro de método é .</span><span class="sxs-lookup"><span data-stu-id="183c6-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="183c6-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="183c6-110">Version introduced</span></span>

<span data-ttu-id="183c6-111">3.0 Pré-visualização 7</span><span class="sxs-lookup"><span data-stu-id="183c6-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="183c6-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="183c6-112">Recommended action</span></span>

<span data-ttu-id="183c6-113">Se o seu código for afetado por essas alterações, você poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="183c6-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="183c6-114">Não há API de `WriteProperty` substituição <xref:System.Text.Json.JsonElement>para as sobrecargas em .</span><span class="sxs-lookup"><span data-stu-id="183c6-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="183c6-115">Em vez disso, você <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> pode chamar <xref:System.Text.Json.JsonElement.WriteTo%2A> uma das sobrecargas junto com o método para alcançar o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="183c6-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="183c6-116">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="183c6-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="183c6-117">Renomeie `WriteValue` <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>o método para .</span><span class="sxs-lookup"><span data-stu-id="183c6-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="183c6-118">O parâmetro do método permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="183c6-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="183c6-119">Por exemplo, o código anterior deve ser alterado para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="183c6-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="183c6-120">Manuseie <xref:System.ArgumentNullException> as <xref:System.Text.Json.JsonElement.WriteTo%2A> chamadas para o método.</span><span class="sxs-lookup"><span data-stu-id="183c6-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="183c6-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="183c6-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
