---
ms.openlocfilehash: 3692848a0cbd4bbbe3c7bb4d2c22a2b19de732e4
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050451"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="34657-101">Construtores não públicos sem parâmetros não usados para desserialização</span><span class="sxs-lookup"><span data-stu-id="34657-101">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="34657-102">Para consistência em todos os monikers de estrutura de destino com suporte (TFMs), não públicos, construtores sem parâmetros não são mais usados para desserialização com <xref:System.Text.Json.JsonSerializer> , por padrão.</span><span class="sxs-lookup"><span data-stu-id="34657-102">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="34657-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="34657-103">Change description</span></span>

<span data-ttu-id="34657-104">OsSystem.Text.Jsautônomos [ em pacotes NuGet](https://www.nuget.org/packages/System.Text.Json/) que dão suporte ao .net Standard 2,0 e superior, ou seja, as versões 4.6.0-4.7.2, se comportam de forma inconsistente com o comportamento interno no .net Core 3,0 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="34657-104">The standalone [System.Text.Json NuGet packages](https://www.nuget.org/packages/System.Text.Json/) that support .NET Standard 2.0 and higher, that is, versions 4.6.0-4.7.2, behave inconsistently with the built-in behavior on .NET Core 3.0 and 3.1.</span></span> <span data-ttu-id="34657-105">No .NET Core 3. x, construtores internos e privados podem ser usados para desserialização.</span><span class="sxs-lookup"><span data-stu-id="34657-105">On .NET Core 3.x, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="34657-106">Nos pacotes autônomos, não são permitidos construtores não públicos, e um <xref:System.MissingMethodException> será gerado se nenhum construtor público sem parâmetros for definido.</span><span class="sxs-lookup"><span data-stu-id="34657-106">In the standalone packages, non-public constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="34657-107">A partir do .NET 5,0 e System.Text.Jsno pacote NuGet 5.0.0, o comportamento é consistente entre o pacote NuGet e as APIs internas.</span><span class="sxs-lookup"><span data-stu-id="34657-107">Starting with .NET 5.0 and System.Text.Json NuGet package 5.0.0, the behavior is consistent between the NuGet package and the built-in APIs.</span></span> <span data-ttu-id="34657-108">Construtores não públicos, incluindo construtores sem parâmetros, são ignorados pelo serializador por padrão.</span><span class="sxs-lookup"><span data-stu-id="34657-108">Non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="34657-109">O serializador usa um dos seguintes construtores para desserialização:</span><span class="sxs-lookup"><span data-stu-id="34657-109">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="34657-110">Construtor público anotado com <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="34657-110">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="34657-111">Construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="34657-111">Public parameterless constructor.</span></span>
- <span data-ttu-id="34657-112">Construtor com parâmetros públicos (se for o único construtor público presente).</span><span class="sxs-lookup"><span data-stu-id="34657-112">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="34657-113">Se nenhum desses construtores estiver disponível, um <xref:System.NotSupportedException> será gerado se você tentar desserializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="34657-113">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="34657-114">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="34657-114">Version introduced</span></span>

<span data-ttu-id="34657-115">5.0</span><span class="sxs-lookup"><span data-stu-id="34657-115">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="34657-116">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="34657-116">Reason for change</span></span>

- <span data-ttu-id="34657-117">Para impor um comportamento consistente entre todos os TFMs (monikers de estrutura de destino) que se <xref:System.Text.Json?displayProperty=fullName> baseiam para o (.NET Core 3,0 e versões posteriores e .NET Standard 2,0)</span><span class="sxs-lookup"><span data-stu-id="34657-117">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions and .NET Standard 2.0)</span></span>
- <span data-ttu-id="34657-118">Porque <xref:System.Text.Json.JsonSerializer> não deve chamar a área da superfície não pública de um tipo, seja um construtor, uma propriedade ou um campo.</span><span class="sxs-lookup"><span data-stu-id="34657-118">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="34657-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="34657-119">Recommended action</span></span>

- <span data-ttu-id="34657-120">Se você possui o tipo e é viável, torne o construtor sem parâmetros público.</span><span class="sxs-lookup"><span data-stu-id="34657-120">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="34657-121">Caso contrário, implemente um `JsonConverter<T>` para o tipo e controle o comportamento de desserialização.</span><span class="sxs-lookup"><span data-stu-id="34657-121">Otherwise, implement a `JsonConverter<T>` for the type and control the deserialization behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="34657-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="34657-122">Category</span></span>

<span data-ttu-id="34657-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="34657-123">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="34657-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="34657-124">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
