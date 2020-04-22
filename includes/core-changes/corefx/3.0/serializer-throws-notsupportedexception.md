---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021662"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="07766-101">Tipo de exceção serializador Json mudou de `JsonException` para`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="07766-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="07766-102">No .NET Core 3.0 Preview 6 a 8, o serializador lançaria um <xref:System.Text.Json.JsonException> quando encontrasse um tipo de coleção derivada sem suporte.</span><span class="sxs-lookup"><span data-stu-id="07766-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="07766-103">Começando no .NET Core 3.0 Preview 9, o serializador lança um <xref:System.NotSupportedException> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="07766-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="07766-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="07766-104">Change description</span></span>

<span data-ttu-id="07766-105">No .NET Core 3.0 Preview 6 até a <xref:System.Text.Json.JsonException> Visualização 8, o serializador lançaria um quando encontrasse um tipo de coleção derivada sem suporte.</span><span class="sxs-lookup"><span data-stu-id="07766-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="07766-106">Um *tipo de coleção derivado sem suporte* é qualquer tipo de coleção que não seja atribuído a um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="07766-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="07766-107">String\<iDictionary,T></span><span class="sxs-lookup"><span data-stu-id="07766-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="07766-108">Começando com .NET Core 3.0 Preview 9, o serializador lança um <xref:System.NotSupportedException> ao encontrar um tipo de coleção sem suporte.</span><span class="sxs-lookup"><span data-stu-id="07766-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="07766-109">O novo tipo de exceção reflete melhor por que a operação de desserialização está falhando.</span><span class="sxs-lookup"><span data-stu-id="07766-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="07766-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="07766-110">Version introduced</span></span>

<span data-ttu-id="07766-111">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="07766-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="07766-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="07766-112">Recommended action</span></span>

<span data-ttu-id="07766-113">Se você está <xref:System.Text.Json.JsonException> pegando ao desserializar, você <xref:System.NotSupportedException>pode querer considerar também pegar .</span><span class="sxs-lookup"><span data-stu-id="07766-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="07766-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="07766-114">Category</span></span>

<span data-ttu-id="07766-115">Bibliotecas Core .NET</span><span class="sxs-lookup"><span data-stu-id="07766-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="07766-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="07766-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
