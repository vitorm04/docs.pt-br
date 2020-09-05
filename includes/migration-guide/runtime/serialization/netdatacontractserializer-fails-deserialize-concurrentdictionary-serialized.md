---
ms.openlocfilehash: 6c120f155660863ce5ae3cf5bd81ea858a68ef8d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496983"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a><span data-ttu-id="88ef5-101">NetDataContractSerializer falha ao desserializar um ConcurrentDictionary serializado com uma versão diferente do .NET</span><span class="sxs-lookup"><span data-stu-id="88ef5-101">NetDataContractSerializer fails to deserialize a ConcurrentDictionary serialized with a different .NET version</span></span>

#### <a name="details"></a><span data-ttu-id="88ef5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="88ef5-102">Details</span></span>

<span data-ttu-id="88ef5-103">Por design, o <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> poderá ser usado somente se as extremidades de serialização e desserialização compartilharem os mesmos tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="88ef5-103">By design, the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="88ef5-104">Portanto, não há garantia de que um objeto serializado com uma versão do .NET Framework poderá ser desserializado com uma versão diferente.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="88ef5-104">Therefore, it is not guaranteed that an object serialized with one version of the .NET Framework can be deserialized by a different version.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span></span> <span data-ttu-id="88ef5-105">é um tipo que não será desserializado corretamente se for serializado com o .NET Framework 4.5 ou anterior e for desserializado com o .NET Framework 4.5.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="88ef5-105">is a type that is known to not to deserialize correctly if serialized with the .NET Framework 4.5 or earlier and deserialized with the .NET Framework 4.5.1 or later.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="88ef5-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="88ef5-106">Suggestion</span></span>

<span data-ttu-id="88ef5-107">Há uma série de possíveis soluções alternativas para esse problema:</span><span class="sxs-lookup"><span data-stu-id="88ef5-107">There are a number of possible work-arounds for this issue:</span></span><ul><li><span data-ttu-id="88ef5-108">Atualizar o computador de serialização para usar o .NET Framework 4.5.1 também.</span><span class="sxs-lookup"><span data-stu-id="88ef5-108">Upgrade the serializing computer to use the .NET Framework 4.5.1, as well.</span></span></li><li><span data-ttu-id="88ef5-109">Usar <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> em vez de <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>, pois ele não espera os mesmos tipos CLR nas extremidades de serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="88ef5-109">Use <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> instead of <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> as this does not expect the exact same CLR types at both serializing and deserializing ends.</span></span></li><li><span data-ttu-id="88ef5-110">Usar <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> em vez de <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>, uma vez que ele não apresenta essa quebra específica entre 4.5 e &gt;4.5.1.</span><span class="sxs-lookup"><span data-stu-id="88ef5-110">Use <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> instead of <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> since it does not exhibit this particular 4.5-&gt;4.5.1 break.</span></span></li></ul>

| <span data-ttu-id="88ef5-111">Nome</span><span class="sxs-lookup"><span data-stu-id="88ef5-111">Name</span></span>    | <span data-ttu-id="88ef5-112">Valor</span><span class="sxs-lookup"><span data-stu-id="88ef5-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="88ef5-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="88ef5-113">Scope</span></span>   |<span data-ttu-id="88ef5-114">Secundária</span><span class="sxs-lookup"><span data-stu-id="88ef5-114">Minor</span></span>|
|<span data-ttu-id="88ef5-115">Versão</span><span class="sxs-lookup"><span data-stu-id="88ef5-115">Version</span></span>|<span data-ttu-id="88ef5-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="88ef5-116">4.5.1</span></span>|
|<span data-ttu-id="88ef5-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="88ef5-117">Type</span></span>|<span data-ttu-id="88ef5-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="88ef5-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="88ef5-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="88ef5-119">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)`

-->
