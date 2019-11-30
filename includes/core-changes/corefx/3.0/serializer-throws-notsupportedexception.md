---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568209"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="6d10c-101">O tipo de exceção do serializador JSON foi alterado de `JsonException` para `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="6d10c-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="6d10c-102">No .NET Core 3,0 Preview 6 a 8, o serializador lançaria um <xref:System.Text.Json.JsonException> quando ele encontrou um tipo de coleção derivada sem suporte.</span><span class="sxs-lookup"><span data-stu-id="6d10c-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="6d10c-103">A partir do .NET Core 3,0 Preview 9, o serializador gera um <xref:System.NotSupportedException> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="6d10c-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6d10c-104">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="6d10c-104">Change description</span></span>

<span data-ttu-id="6d10c-105">No .NET Core 3,0 Preview 6 até a versão prévia 8, o serializador lançaria um <xref:System.Text.Json.JsonException> quando ele encontrou um tipo de coleção derivada sem suporte.</span><span class="sxs-lookup"><span data-stu-id="6d10c-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="6d10c-106">Um *tipo de coleção derivada sem suporte* é qualquer tipo de coleção que não seja atribuível a um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="6d10c-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="6d10c-107">IDictionary\<cadeia de caracteres, T ></span><span class="sxs-lookup"><span data-stu-id="6d10c-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="6d10c-108">A partir do .NET Core 3,0 Preview 9, o serializador gera um <xref:System.NotSupportedException> ao encontrar um tipo de coleção sem suporte.</span><span class="sxs-lookup"><span data-stu-id="6d10c-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="6d10c-109">O novo tipo de exceção melhor reflete por que a operação de desserialização está falhando.</span><span class="sxs-lookup"><span data-stu-id="6d10c-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6d10c-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="6d10c-110">Version introduced</span></span>

<span data-ttu-id="6d10c-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="6d10c-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6d10c-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="6d10c-112">Recommended action</span></span>

<span data-ttu-id="6d10c-113">Se estiver capturando <xref:System.Text.Json.JsonException> ao desserializar, talvez você queira considerar também a possibilidade de detectar <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="6d10c-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="6d10c-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="6d10c-114">Category</span></span>

<span data-ttu-id="6d10c-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="6d10c-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6d10c-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6d10c-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
