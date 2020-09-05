---
ms.openlocfilehash: ccba3cf98a1ca9e199d9a48f00e254bf34b93f72
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496119"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a><span data-ttu-id="05768-101">BinaryFormatter pode não conseguir localizar o tipo do contexto LoadFrom</span><span class="sxs-lookup"><span data-stu-id="05768-101">BinaryFormatter can fail to find type from LoadFrom context</span></span>

#### <a name="details"></a><span data-ttu-id="05768-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="05768-102">Details</span></span>

<span data-ttu-id="05768-103">A partir do .NET Framework 4.5, várias alterações de <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> podem causar diferenças na desserialização ao usar <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> para desserializar tipos que foram carregados no contexto LoadFrom.</span><span class="sxs-lookup"><span data-stu-id="05768-103">As of .NET Framework 4.5, a number of <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> changes may cause differences in deserialization when using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> to deserialize types that had been loaded in the LoadFrom context.</span></span> <span data-ttu-id="05768-104">Essas alterações se devem a novas maneiras como <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> agora carrega um tipo, o que causa um comportamento diferente quando um <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> tenta desserializar esse tipo posteriormente.</span><span class="sxs-lookup"><span data-stu-id="05768-104">These changes are due to the new ways <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> now loads a type which causes different behavior when a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> attempts to deserialize to that type later on.</span></span> <span data-ttu-id="05768-105">O associador de serialização padrão não pesquisa automaticamente o contexto LoadFrom, embora isso possa ter funcionado em algumas circunstâncias com base no comportamento antigo do XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="05768-105">The default serialization binder does not automatically search the LoadFrom context, although it may have worked in some circumstances based on the old behavior of XmlSerializer.</span></span> <span data-ttu-id="05768-106">Devido às alterações, quando um tipo está sendo carregado de um assembly carregado em um contexto diferente, um <xref:System.IO.FileNotFoundException?displayProperty=fullName> pode ser acionado.</span><span class="sxs-lookup"><span data-stu-id="05768-106">Due to the changes, when a type is being loaded from an assembly loaded in a different context, a <xref:System.IO.FileNotFoundException?displayProperty=fullName> may be thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="05768-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="05768-107">Suggestion</span></span>

<span data-ttu-id="05768-108">Se essa exceção for observada, a propriedade <code>Binder</code> do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> poderá ser definida como um associador personalizado que encontrará o tipo correto.</span><span class="sxs-lookup"><span data-stu-id="05768-108">If this exception is seen, the <code>Binder</code> property of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> can be set to a custom binder that will find the correct type.</span></span><pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre><span data-ttu-id="05768-109">E, em seguida, o associador personalizado:</span><span class="sxs-lookup"><span data-stu-id="05768-109">And then the custom binder:</span></span><pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="05768-110">Nome</span><span class="sxs-lookup"><span data-stu-id="05768-110">Name</span></span>    | <span data-ttu-id="05768-111">Valor</span><span class="sxs-lookup"><span data-stu-id="05768-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="05768-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="05768-112">Scope</span></span>   |<span data-ttu-id="05768-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="05768-113">Edge</span></span>|
|<span data-ttu-id="05768-114">Versão</span><span class="sxs-lookup"><span data-stu-id="05768-114">Version</span></span>|<span data-ttu-id="05768-115">4.5</span><span class="sxs-lookup"><span data-stu-id="05768-115">4.5</span></span>|
|<span data-ttu-id="05768-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="05768-116">Type</span></span>|<span data-ttu-id="05768-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="05768-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="05768-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="05768-118">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
