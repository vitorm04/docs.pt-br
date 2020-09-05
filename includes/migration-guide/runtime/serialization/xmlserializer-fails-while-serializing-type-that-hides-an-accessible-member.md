---
ms.openlocfilehash: 75c7385bceec2595683d1c0d97a7df9264e3bf0b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497813"
---
### <a name="xmlserializer-fails-while-serializing-a-type-that-hides-an-accessible-member-with-an-inaccessible-one"></a><span data-ttu-id="db32d-101">XmlSerializer falha durante a serialização de um tipo que oculta um membro acessível com um inacessível</span><span class="sxs-lookup"><span data-stu-id="db32d-101">XmlSerializer fails while serializing a type that hides an accessible member with an inaccessible one</span></span>

#### <a name="details"></a><span data-ttu-id="db32d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="db32d-102">Details</span></span>

<span data-ttu-id="db32d-103">Ao serializar um tipo derivado, o <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> pode falhar se o tipo contiver um campo ou propriedade inacessível que oculta (por meio da palavra-chave "new") um campo ou propriedade do mesmo nome que estava acessível anteriormente (público, por exemplo) no tipo base.</span><span class="sxs-lookup"><span data-stu-id="db32d-103">When serializing a derived type, the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> can fail if the type contains an inaccessible field or property that hides (via the 'new' keyword) a field or property of the same name that was previously accessible (public, for example) on the base type.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="db32d-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="db32d-104">Suggestion</span></span>

<span data-ttu-id="db32d-105">Esse problema pode ser resolvido tornando o novo membro oculto acessível para o <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (marcando-o como público, por exemplo). Como alternativa, a seguinte configuração será revertida para o comportamento <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> no 4.0, o que corrigirá o problema:</span><span class="sxs-lookup"><span data-stu-id="db32d-105">This problem can be solved by making the new, hiding member accessible to the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (by marking it public, for example).Alternatively, the following config setting will revert to 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> behavior, which will fix the problem:</span></span><pre><code class="lang-xml">&lt;system.xml.serialization&gt;&#13;&#10;&lt;xmlSerializer useLegacySerializerGeneration=&quot;true&quot; /&gt;&#13;&#10;&lt;/system.xml.serialization&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="db32d-106">Nome</span><span class="sxs-lookup"><span data-stu-id="db32d-106">Name</span></span>    | <span data-ttu-id="db32d-107">Valor</span><span class="sxs-lookup"><span data-stu-id="db32d-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="db32d-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="db32d-108">Scope</span></span>   |<span data-ttu-id="db32d-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="db32d-109">Minor</span></span>|
|<span data-ttu-id="db32d-110">Versão</span><span class="sxs-lookup"><span data-stu-id="db32d-110">Version</span></span>|<span data-ttu-id="db32d-111">4.5</span><span class="sxs-lookup"><span data-stu-id="db32d-111">4.5</span></span>|
|<span data-ttu-id="db32d-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="db32d-112">Type</span></span>|<span data-ttu-id="db32d-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="db32d-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="db32d-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="db32d-114">Affected APIs</span></span>

- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)`

-->
