---
ms.openlocfilehash: 572ebc47d26e30738fc4e5b8a8fab1f2643e3d83
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997726"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="fa6ed-101">Construtores não públicos sem parâmetros não usados para desserialização</span><span class="sxs-lookup"><span data-stu-id="fa6ed-101">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="fa6ed-102">Para consistência em todos os monikers de estrutura de destino com suporte (TFMs), não públicos, construtores sem parâmetros não são mais usados para desserialização com <xref:System.Text.Json.JsonSerializer> , por padrão.</span><span class="sxs-lookup"><span data-stu-id="fa6ed-102">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fa6ed-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="fa6ed-103">Change description</span></span>

<span data-ttu-id="fa6ed-104">No .NET Core 3,0 e 3,1, construtores internos e privados podem ser usados para desserialização.</span><span class="sxs-lookup"><span data-stu-id="fa6ed-104">On .NET Core 3.0 and 3.1, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="fa6ed-105">Em .NET Standard 2,0 e 2,1, construtores internos e privados não são permitidos e um <xref:System.MissingMethodException> será gerado se nenhum construtor público sem parâmetros for definido.</span><span class="sxs-lookup"><span data-stu-id="fa6ed-105">On .NET Standard 2.0 and 2.1, internal and private constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="fa6ed-106">A partir do .NET 5,0, os construtores não públicos, incluindo construtores sem parâmetros, são ignorados pelo serializador por padrão.</span><span class="sxs-lookup"><span data-stu-id="fa6ed-106">Starting in .NET 5.0, non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="fa6ed-107">O serializador usa um dos seguintes construtores para desserialização:</span><span class="sxs-lookup"><span data-stu-id="fa6ed-107">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="fa6ed-108">Construtor público anotado com <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="fa6ed-108">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="fa6ed-109">Construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fa6ed-109">Public parameterless constructor.</span></span>
- <span data-ttu-id="fa6ed-110">Construtor com parâmetros públicos (se for o único construtor público presente).</span><span class="sxs-lookup"><span data-stu-id="fa6ed-110">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="fa6ed-111">Se nenhum desses construtores estiver disponível, um <xref:System.NotSupportedException> será gerado se você tentar desserializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="fa6ed-111">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fa6ed-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fa6ed-112">Version introduced</span></span>

<span data-ttu-id="fa6ed-113">5.0</span><span class="sxs-lookup"><span data-stu-id="fa6ed-113">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fa6ed-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="fa6ed-114">Reason for change</span></span>

- <span data-ttu-id="fa6ed-115">Para impor um comportamento consistente entre todos os TFMs (monikers de estrutura de destino) que se <xref:System.Text.Json?displayProperty=fullName> baseiam para o (.NET Core 3,0 e versões posteriores e .NET Standard 2,0 e 2,1)</span><span class="sxs-lookup"><span data-stu-id="fa6ed-115">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions, and .NET Standard 2.0 and 2.1)</span></span>
- <span data-ttu-id="fa6ed-116">Porque <xref:System.Text.Json.JsonSerializer> não deve chamar a área da superfície não pública de um tipo, seja um construtor, uma propriedade ou um campo.</span><span class="sxs-lookup"><span data-stu-id="fa6ed-116">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fa6ed-117">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fa6ed-117">Recommended action</span></span>

- <span data-ttu-id="fa6ed-118">Se você possui o tipo e é viável, torne o construtor sem parâmetros público.</span><span class="sxs-lookup"><span data-stu-id="fa6ed-118">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="fa6ed-119">Caso contrário, implemente um `JsonConverter<T>` para o tipo e controle o comportamento de desserialização.</span><span class="sxs-lookup"><span data-stu-id="fa6ed-119">Otherwise, implement a `JsonConverter<T>` for the type and control the deserialization behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="fa6ed-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="fa6ed-120">Category</span></span>

<span data-ttu-id="fa6ed-121">Serialização</span><span class="sxs-lookup"><span data-stu-id="fa6ed-121">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fa6ed-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fa6ed-122">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
