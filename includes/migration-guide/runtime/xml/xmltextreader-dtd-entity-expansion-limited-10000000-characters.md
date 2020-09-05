---
ms.openlocfilehash: e56d896f093d6cd28ed0d6640ba154e5d4593c6d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496978"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a><span data-ttu-id="0182d-101">Expansão da entidade DTD de XmlTextReader é limitada a 10.000.000 caracteres</span><span class="sxs-lookup"><span data-stu-id="0182d-101">XmlTextReader DTD entity expansion is limited to 10,000,000 characters</span></span>

#### <a name="details"></a><span data-ttu-id="0182d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0182d-102">Details</span></span>

<span data-ttu-id="0182d-103">A expansão da entidade DTD agora é limitada a 10.000.000 de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0182d-103">DTD entity expansion is now limited to 10,000,000 characters.</span></span> <span data-ttu-id="0182d-104">O carregamento de arquivos XML sem expansão de entidade DTD ou com expansão de entidade DTD limitada não é afetado.</span><span class="sxs-lookup"><span data-stu-id="0182d-104">Loading XML files without DTD entity expansion or with limited DTD entity expansion is unaffected.</span></span> <span data-ttu-id="0182d-105">Arquivos com entidades DTD que se expandem para mais de 10.000.000 caracteres falham ao carregar e geram uma exceção.</span><span class="sxs-lookup"><span data-stu-id="0182d-105">Files with DTD entities that expand to more than 10,000,000 characters fail to load, and now throw an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0182d-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="0182d-106">Suggestion</span></span>

<span data-ttu-id="0182d-107">Se o limite da expansão da entidade DTD for muito inferior a 10.000.000, o valor poderá ser substituído pela propriedade <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities>.</span><span class="sxs-lookup"><span data-stu-id="0182d-107">If the limit of DTD entity expansion is too low 10,000,000, the value can be overridden with the <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> property.</span></span> <span data-ttu-id="0182d-108">Um <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> com o valor <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> correto pode ser passado para o <code>XmlReader.Create</code> que usa <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (por exemplo, <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>).</span><span class="sxs-lookup"><span data-stu-id="0182d-108">An <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> with the proper <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> value can be passed to <code>XmlReader.Create</code> that takes <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (ie. <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)</span></span>

| <span data-ttu-id="0182d-109">Nome</span><span class="sxs-lookup"><span data-stu-id="0182d-109">Name</span></span>    | <span data-ttu-id="0182d-110">Valor</span><span class="sxs-lookup"><span data-stu-id="0182d-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0182d-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="0182d-111">Scope</span></span>   |<span data-ttu-id="0182d-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="0182d-112">Edge</span></span>|
|<span data-ttu-id="0182d-113">Versão</span><span class="sxs-lookup"><span data-stu-id="0182d-113">Version</span></span>|<span data-ttu-id="0182d-114">4.5</span><span class="sxs-lookup"><span data-stu-id="0182d-114">4.5</span></span>|
|<span data-ttu-id="0182d-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="0182d-115">Type</span></span>|<span data-ttu-id="0182d-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="0182d-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="0182d-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0182d-117">Affected APIs</span></span>

- <xref:System.Xml.XmlTextReader?displayProperty=nameWithType>
- <xref:System.Xml.XmlTextReader.%23ctor>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)>

<!--

#### Affected APIs

- `T:System.Xml.XmlTextReader`
- `M:System.Xml.XmlTextReader.#ctor`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.TextReader)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.TextReader,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.Stream)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.TextReader)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)`
- `M:System.Xml.XmlTextReader.#ctor(System.Xml.XmlNameTable)`

-->
