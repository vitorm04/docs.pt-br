---
ms.openlocfilehash: 5a3370e71488e4f9d8d933b504d1d771c78e0385
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619810"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a><span data-ttu-id="031a9-101">SoapFormatter não pode desserializar Hashtable e objetos de coleção ordenados semelhantes</span><span class="sxs-lookup"><span data-stu-id="031a9-101">SoapFormatter cannot deserialize Hashtable and similar ordered collection objects</span></span>

#### <a name="details"></a><span data-ttu-id="031a9-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="031a9-102">Details</span></span>

<span data-ttu-id="031a9-103">O <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> não garante que objetos serializados em uma versão do .NET Framework serão desserializados com êxito em uma versão diferente.</span><span class="sxs-lookup"><span data-stu-id="031a9-103">The <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> does not guarantee that objects serialized under one .NET Framework version will successfully deserialize under a different version.</span></span> <span data-ttu-id="031a9-104">Especificamente, algumas coleções ordenadas (como <xref:System.Collections.Hashtable?displayProperty=fullName>) tiveram membros adicionados entre a 4.0 e a 4.5, portanto, os objetos desses tipos não poderão ser desserializados com o .NET Framework 4.0 se tiverem sido serializados com o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="031a9-104">Specifically, some ordered collections (like <xref:System.Collections.Hashtable?displayProperty=fullName>) added members between 4.0 and 4.5 such that objects of these types cannot deserialize with .NET Framework 4.0 if they were serialized with .NET Framework 4.5.</span></span> <span data-ttu-id="031a9-105">Observe que se os dados serializados forem serializados e desserializados com a mesma versão do .NET Framework, nenhum problema ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="031a9-105">Note that if the serialized data is both serialized and deserialized with the same .NET Framework version, no issue will occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="031a9-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="031a9-106">Suggestion</span></span>

<span data-ttu-id="031a9-107">A serialização <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> deve ser substituída pela serialização <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> ou <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> para resistir às alterações do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="031a9-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> serialization should be replaced with <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serialization or <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> to be resilient to .NET Framework changes.</span></span>

| <span data-ttu-id="031a9-108">Name</span><span class="sxs-lookup"><span data-stu-id="031a9-108">Name</span></span>    | <span data-ttu-id="031a9-109">Valor</span><span class="sxs-lookup"><span data-stu-id="031a9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="031a9-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="031a9-110">Scope</span></span>   |<span data-ttu-id="031a9-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="031a9-111">Minor</span></span>|
|<span data-ttu-id="031a9-112">Versão</span><span class="sxs-lookup"><span data-stu-id="031a9-112">Version</span></span>|<span data-ttu-id="031a9-113">4.5</span><span class="sxs-lookup"><span data-stu-id="031a9-113">4.5</span></span>|
|<span data-ttu-id="031a9-114">Type</span><span class="sxs-lookup"><span data-stu-id="031a9-114">Type</span></span>|<span data-ttu-id="031a9-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="031a9-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="031a9-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="031a9-116">Affected APIs</span></span>

-<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
