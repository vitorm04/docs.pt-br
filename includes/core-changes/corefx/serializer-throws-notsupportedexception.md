---
ms.openlocfilehash: 39d1b2dba8077bf9bf998775f8967d455f36b549
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119278"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="ad421-101">Tipo de exceção do serializador `JsonException` JSON alterado de para`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="ad421-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="ad421-102">No .NET Core 3,0 Preview 6 a 8, o serializador geraria <xref:System.Text.Json.JsonException> um quando ele encontrou um tipo de coleção derivada sem suporte.</span><span class="sxs-lookup"><span data-stu-id="ad421-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="ad421-103">A partir do .NET Core 3,0 Preview 9, o serializador <xref:System.NotSupportedException> gera um em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ad421-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ad421-104">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="ad421-104">Change description</span></span>

<span data-ttu-id="ad421-105">No .NET Core 3,0 Preview 6 até a versão prévia 8, o serializador <xref:System.Text.Json.JsonException> geraria um quando ele encontrou um tipo de coleção derivada sem suporte.</span><span class="sxs-lookup"><span data-stu-id="ad421-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="ad421-106">Um *tipo de coleção derivada sem suporte* é qualquer tipo de coleção que não seja atribuível a um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="ad421-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

 - <xref:System.Collections.IList>
 - <xref:System.Collections.Generic.ICollection%601>
 - <xref:System.Collections.Generic.Stack%601>
 - <xref:System.Collections.Generic.Queue%601>`
 - <xref:System.Collections.IDictionary>
 - [<span data-ttu-id="ad421-107">Cadeia\<de caracteres IDictionary, T ></span><span class="sxs-lookup"><span data-stu-id="ad421-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="ad421-108">A partir do .NET Core 3,0 Preview 9, o serializador <xref:System.NotSupportedException> gera um ao encontrar um tipo de coleção sem suporte.</span><span class="sxs-lookup"><span data-stu-id="ad421-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="ad421-109">O novo tipo de exceção melhor reflete por que a operação de desserialização está falhando.</span><span class="sxs-lookup"><span data-stu-id="ad421-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ad421-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ad421-110">Version introduced</span></span>

<span data-ttu-id="ad421-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="ad421-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ad421-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ad421-112">Recommended action</span></span>

<span data-ttu-id="ad421-113">Se você estiver <xref:System.Text.Json.JsonException> se deparando ao desserializar, convém considerar também <xref:System.NotSupportedException>a captura.</span><span class="sxs-lookup"><span data-stu-id="ad421-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="ad421-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="ad421-114">Category</span></span>

<span data-ttu-id="ad421-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="ad421-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ad421-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ad421-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
