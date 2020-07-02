---
ms.openlocfilehash: eafbdd2d42977381fb4d77748a3c9a2595ff2936
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619809"
---
### <a name="xmlserializer-fails-while-serializing-a-type-that-hides-an-accessible-member-with-an-inaccessible-one"></a><span data-ttu-id="23bc2-101">XmlSerializer falha durante a serialização de um tipo que oculta um membro acessível com um inacessível</span><span class="sxs-lookup"><span data-stu-id="23bc2-101">XmlSerializer fails while serializing a type that hides an accessible member with an inaccessible one</span></span>

#### <a name="details"></a><span data-ttu-id="23bc2-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="23bc2-102">Details</span></span>

<span data-ttu-id="23bc2-103">Ao serializar um tipo derivado, o <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> pode falhar se o tipo contiver um campo ou propriedade inacessível que oculta (por meio da palavra-chave "new") um campo ou propriedade do mesmo nome que estava acessível anteriormente (público, por exemplo) no tipo base.</span><span class="sxs-lookup"><span data-stu-id="23bc2-103">When serializing a derived type, the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> can fail if the type contains an inaccessible field or property that hides (via the 'new' keyword) a field or property of the same name that was previously accessible (public, for example) on the base type.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="23bc2-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="23bc2-104">Suggestion</span></span>

<span data-ttu-id="23bc2-105">Esse problema pode ser resolvido tornando o novo membro oculto acessível para o <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (marcando-o como público, por exemplo). Como alternativa, a seguinte configuração será revertida para o comportamento <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> no 4.0, o que corrigirá o problema:</span><span class="sxs-lookup"><span data-stu-id="23bc2-105">This problem can be solved by making the new, hiding member accessible to the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (by marking it public, for example).Alternatively, the following config setting will revert to 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> behavior, which will fix the problem:</span></span><pre><code class="lang-xml">&lt;system.xml.serialization&gt;&#13;&#10;&lt;xmlSerializer useLegacySerializerGeneration=&quot;true&quot; /&gt;&#13;&#10;&lt;/system.xml.serialization&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="23bc2-106">Name</span><span class="sxs-lookup"><span data-stu-id="23bc2-106">Name</span></span>    | <span data-ttu-id="23bc2-107">Valor</span><span class="sxs-lookup"><span data-stu-id="23bc2-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="23bc2-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="23bc2-108">Scope</span></span>   |<span data-ttu-id="23bc2-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="23bc2-109">Minor</span></span>|
|<span data-ttu-id="23bc2-110">Versão</span><span class="sxs-lookup"><span data-stu-id="23bc2-110">Version</span></span>|<span data-ttu-id="23bc2-111">4.5</span><span class="sxs-lookup"><span data-stu-id="23bc2-111">4.5</span></span>|
|<span data-ttu-id="23bc2-112">Type</span><span class="sxs-lookup"><span data-stu-id="23bc2-112">Type</span></span>|<span data-ttu-id="23bc2-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="23bc2-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="23bc2-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="23bc2-114">Affected APIs</span></span>

-<xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)?displayProperty=nameWithType></li></ul>|
